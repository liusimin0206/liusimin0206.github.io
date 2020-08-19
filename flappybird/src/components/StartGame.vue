<template>
  <div class="startGame">
    <div class="title">
      <Bird
        :isStartGame="isStartGame"
        :isStartbirdJump="isStartbirdJump"
        :minTopOfBird="0"
        :maxTopOfBird="50"
      ></Bird>
      <div
        class="startGameButton"
        @click="startGame"
        :class="[switchtruthiness ? 'white' : 'blue']"
      >
        开始游戏
      </div>
    </div>
  </div>
</template>

<script>
import Bird from "./Bird";
export default {
  data() {
    return {
      isStartGame: false,

      switchtruthiness: true
    };
  },
  components: {
    Bird
  },
  props: {
    handleTimes: Number
  },
  methods: {
    startGame() {
      this.isStartGame = true;
      this.$emit("StartGame", true);
    },
    startBound() {
      this.switchtruthiness = !this.switchtruthiness;
    }
  },
  watch: {
    isStartbirdJump: function(newVal) {
      if (newVal) {
        this.startBound();
      }
    }
  },
  computed: {
    topOfBirdStr: function() {
      return this.topOfBird + "px";
    },
    isStartbirdJump() {
      return this.handleTimes % 10 === 0;
    }
  }
};
</script>

<style scoped lang="scss">
.startGame {
  .title {
    position: fixed;
    width: 150px;
    height: 150px;
    margin: auto;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    .startGameButton {
      position: absolute;
      width: 150px;
      height: 60px;
      line-height: 60px;
      left: 50%;
      top: 90px;
      transform: translateX(-50%);
      text-align: center;
      font-weight: bolder;
      transition: all 0.3s linear;
      cursor: pointer;
    }
    .startGameButton.white {
      color: #fff;
      font-size: 24px;
    }
    .startGameButton.blue {
      color: #09f;
      font-size: 36px;
    }
  }
}
</style>
