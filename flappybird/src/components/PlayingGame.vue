<template>
  <div class="playingGame" @click="handleGameClick">
    <div class="score">0</div>
    <div class="location">
      <div class="locateY">
        <Bird
          :isStartGame="isStartGame"
          :isActive="isActive"
          :isStartbirdJump="false"
          :handleTimes="handleTimes"
          ref="bird"
        ></Bird>
      </div>
    </div>
  </div>
</template>

<script>
import Bird from "./Bird";
export default {
  data() {
    return {};
  },
  components: { Bird },
  methods: {
    handleGameClick() {
      this.$refs.bird.birdClickJump();
    }
  },
  props: {
    isStartGame: Boolean,
    handleTimes: Number,
    appClick: Boolean
  },
  computed: {
    isActive() {
      return this.handleTimes % 10 === 0;
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
    .locateY {
      position: absolute;
    }
  }
}
</style>
