<template>
  <div class="endGame">
    <div class="title">
      <div class="over">Game over</div>
      <div class="result">Your Results:</div>
      <div class="final-score">0</div>
      <ul class="rank-list">
        <li v-for="item in gameRecording" :key="item.key" class="rank-item">
          <span class="rank-degree">{{ item.rank }}</span>
          <span class="rank-score">{{ item.score }}</span>
          <span class="rank-time">{{ item.time }}</span>
        </li>
      </ul>
      <div class="restart" @click="restart">重新开始</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      gameRecording: [
        { rank: 1, score: 0, time: "2020.08.15 20:20:20", key: 0 },
        { rank: 2, score: 0, time: "2020.08.15 20:20:20", key: 1 }
      ]
    };
  },
  methods: {
    restart() {
      this.$emit("restart", true);
    }
  }
};
</script>

<style scoped lang="scss">
.endGame {
  .title {
    position: fixed;
    width: 150px;
    height: 150px;
    margin: auto;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
  }
}
</style>
