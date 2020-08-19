<template>
  <div id="app" :style="{ backgroundPositionX: backgroundMoveXStr }">
    <StartGame
      :handleTimes="this.handleTimes"
      @StartGame="handleStartGame"
      v-if="!isStartGame"
    ></StartGame>
    <PlayingGame :isStartGame="isStartGame" v-if="isStartGame"></PlayingGame>
    <EndGame></EndGame>
  </div>
</template>

<script>
import StartGame from "@/components/StartGame";
import EndGame from "@/components/EndGame";
import PlayingGame from "@/components/PlayingGame";
export default {
  name: "App",
  components: { StartGame, EndGame, PlayingGame },
  data() {
    return {
      backgroundMoveSpeed: 2,
      backgroundMoveX: 0,
      handleTimes: 0,
      isStartGame: false
    };
  },
  created() {
    setInterval(() => {
      this.handleTimes++;
      this.backgroundMoveX -= this.backgroundMoveSpeed;
    }, 30);
  },
  computed: {
    backgroundMoveXStr: function() {
      return this.backgroundMoveX + "px";
    }
  },
  methods: {
    handleStartGame(val) {
      this.isStartGame = val;
    }
  }
};
</script>

<style lang="scss">
#app {
  position: relative;
  height: 100%;
  background-image: url("./assets/img/sky1.png");
  // background-position-x: 0;
  background-repeat: repeat-x;
  background-size: contain;
  // background-repeat: no-repeat;
  background-attachment: fixed;
}
</style>
