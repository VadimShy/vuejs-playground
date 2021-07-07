<template>
  <div class="main">
    <div class="main__container">

      <div class="result-element">
        <span class="result-element__percents">{{ convertToPercent(sad) }}</span>
        <span class="result-element__product">Препарат 1</span>
      </div>

      <div class="result-element">
        <span class="result-element__percents">{{ convertToPercent(happy) }}</span>
        <span class="result-element__product">Препарат 2</span>
      </div>
      <div class="result-element">
        <span class="result-element__percents">{{ convertToPercent(love) }}</span>
        <span class="result-element__product">Препарат 3</span>
      </div>

      <div class="separator" />
    </div>

    <div class="result">
      <p class="result-text-1">Ваш результат: </p>
      <p class="result-text-2">"Что я здесь делаю"?</p>
      <p class="result-text-3">Это тестовое задание, так что не
        будем <br> углубляться в глубины проблем фармавцевтов</p>

    </div>
  </div>
  <img class="image-end" src="../assets/end.png"/>

  <button
    class="home-button"
    @click="$emit('restartGame');">
    <img src="../assets/btn-home.png"/>

  </button>

  <button
    class="home-button-2"
    @click="$emit('restartGame');">
    Попробовать еще

  </button>

</template>

<script>
export default {
  props: {
    happy: Number,
    sad: Number,
    love: Number,

    isEnd: Boolean,
  },
  methods: {
    convertToPercent(a) {
      return `${a}%`;
    },

  },
};
</script>

<style lang="scss" rel="stylesheet/scss">
@import './component-styles/resultScreen.scss';
</style>
