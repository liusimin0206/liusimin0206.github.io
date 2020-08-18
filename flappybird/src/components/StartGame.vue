<template>
  <div class="startGame" :class="{ displayNone: isStartGame }">
    <div class="title">
      <div class="bird" :style="{ top: this.topOfBirdStr }"></div>
      <div class="startGameButton" @click="isStartGame = true">开始游戏</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isStartGame: false,
      minTopOfBird: 0,
      maxTopOfBird: 50,
      topOfBird: 0
    };
  },
  props: {
    handleTimes: Number
  },
  methods: {},
  watch: {
    handleTimes: function(newVal) {
      if (newVal % 10 === 0) {
        this.topOfBird =
          this.topOfBird === this.maxTopOfBird
            ? this.minTopOfBird
            : this.maxTopOfBird;
      }
    }
  },
  computed: {
    topOfBirdStr: function() {
      return this.topOfBird + "px";
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
    .bird {
      position: absolute;
      left: 50%;
      top: 30px;
      width: 30px;
      height: 30px;
      margin-left: -15px;
      background-image: url("../assets/img/birds.png");
      transition: top 0.3s linear;
    }
    .startGameButton {
      position: absolute;
      width: 150px;
      left: 50%;
      top: 80px;
      margin-left: -75px;
      text-align: center;
    }
  }
}
</style>
