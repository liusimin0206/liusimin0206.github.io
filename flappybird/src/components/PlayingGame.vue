<template>
  <div class="playingGame" @click="handleGameClick">
    <div class="score">0</div>
    <div class="location">
      <div class="pipeUp"></div>
      <div class="pipeDown"></div>
      <div class="locateY" :style="{ top: locateY2Str }">
        <Bird
          :isStartGame="isStartGame"
          :isActive="isActive"
          :isStartbirdJump="false"
        ></Bird>
      </div>
    </div>
  </div>
</template>

<script>
import Bird from "./Bird";
export default {
  data() {
    return { locateY: 0, dropStepY: 0, bodyHeight: 1000 };
  },
  components: { Bird },
  methods: {
    handleGameClick() {
      this.dropStepY = -10;
    },
    dropLocateY() {
      this.locateY += ++this.dropStepY;
    },
    judgeKnock() {
      this.judgeBoundary();
      this.judgePipe();
    },
    judgeBoundary() {
      if (this.locateY <= this.minTop || this.locateY >= this.maxTop) {
        this.failGame();
      }
    },
    judgePipe() {},
    failGame() {
      console.log("game over");
      this.$emit("gameOver", false);
    }
  },
  props: {
    isStartGame: Boolean,
    handleTimes: Number,
    appClick: Boolean
  },
  mounted() {
    this.bodyHeight = document.body.scrollHeight;
  },
  computed: {
    isActive() {
      return this.handleTimes % 10 === 0;
    },
    locateY2Str() {
      return this.locateY + "px";
    },
    minTop() {
      return -(this.bodyHeight / 2 - 10);
    },
    maxTop() {
      return this.bodyHeight / 2 + 10;
    }
  },
  watch: {
    handleTimes() {
      this.dropLocateY();
      this.judgeKnock();
    }
  }
};
</script>

<style scoped lang="scss">
.playingGame {
  height: 100%;
  .score {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    font-size: 20px;
    font-weight: bolder;
    color: #fff;
    user-select: none;
  }
  .location {
    position: absolute;
    width: 30px;
    height: 30px;
    left: 25%;
    top: 50%;
    transform: translate(-50%, -50%);
    .pipeUp {
      position: absolute;
      width: 30px;
      height: 300px;
      background-color: red;
    }
    .pipeDown {
      position: absolute;
      width: 30px;
      height: 300px;
      background-color: red;
    }
    .locateY {
      position: absolute;
    }
  }
}
</style>
