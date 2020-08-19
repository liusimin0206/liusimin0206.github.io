<template>
  <div>
    <div class="score">0</div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {}
};
</script>

<style scoped lang="scss">
.score {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  font-size: 20px;
  font-weight: bolder;
  color: #fff;
}
</style>
