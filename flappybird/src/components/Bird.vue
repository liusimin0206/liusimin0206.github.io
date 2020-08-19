<template>
  <div>
    <div
      class="bird"
      :style="{
        top: this.topOfBird2Str,
        backgroundPositionX: backgroundPositionX2Str
      }"
    ></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      topOfBird: 0,
      backgroundPositionX: 0
    };
  },
  props: {
    isStartGame: Boolean,
    isStartbirdJump: Boolean,
    minTopOfBird: Number,
    maxTopOfBird: Number
  },
  methods: {
    startbirdJump() {
      this.topOfBird =
        this.topOfBird === this.maxTopOfBird
          ? this.minTopOfBird
          : this.maxTopOfBird;
    },
    birdfly() {
      if (this.backgroundPositionX <= -60) {
        this.backgroundPositionX = 0;
      } else this.backgroundPositionX -= 30;
    }
  },
  computed: {
    topOfBird2Str: function() {
      return this.topOfBird + "px";
    },
    backgroundPositionX2Str: function() {
      return this.backgroundPositionX + "px";
    }
  },
  watch: {
    isStartbirdJump: {
      handler(newVal) {
        if (newVal) {
          this.startbirdJump();
          this.birdfly();
        }
      },
      immediate: true
    }
  }
};
</script>

<style scoped lang="scss">
.bird {
  position: absolute;
  left: 50%;
  top: 30px;
  width: 30px;
  height: 30px;
  transform: translateX(-50%);
  background-image: url("../assets/img/birds.png");
  transition: top 0.3s linear;
}
</style>
