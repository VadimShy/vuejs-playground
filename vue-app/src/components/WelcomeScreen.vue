<template>
  <div class="container-bg">
    <div class="grad"></div>
    <div class="circle">
      <div class="circle-container">
        <span class="text-small">Добро пожаловать в игру</span>
        <span class="text-big">{{ `Помоги \n ФАРМАЦЕВТУ` }}</span>
        <button
          class="startButton"
          v-on:click="$emit('update:modelValue', false)">
          Начать
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    isStarted: Boolean,
  },
};
</script>

<style lang="scss" rel="stylesheet/scss">
 @import './component-styles/WelcomeScreen.scss';
</style>
