<template>
  <div class="card">
   <img :src="image"/>
    <div class="card__text">
      <p class="card__title">{{title}}</p>
      <p class="card__title-text">{{text}}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    text: String,
    image: String,
  },
};

</script>

<style lang="scss" rel="stylesheet/scss">
  @import'./component-styles/card.scss';
</style>
