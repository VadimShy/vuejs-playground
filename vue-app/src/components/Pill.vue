<template>
  <div class="pill">
    <img class="pill__emoji" :src="image"/>
    <span class="pill__counter"><b>{{count}}</b></span>
  </div>
</template>

<script>
export default {
  props: {
    count: Number,
    image: String,
  },
};
</script>

<style lang="scss" rel="stylesheet/scss">
  @import'./component-styles/pill.scss';
</style>
