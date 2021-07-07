<template>
  <div class="counter">
    <p class="counter__text">Осталось в очереди:</p>
    <span class="counter__numbers"><b>{{current}}</b> / {{total}}</span>
  </div>
</template>

<script>
export default {
  props: {
    current: Number,
    total: Number,
  },
};
</script>

<style lang="scss" rel="stylesheet/scss">
  @import'./component-styles/counter.scss';
</style>
