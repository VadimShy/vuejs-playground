<template>
  <button v-bind:class="classObject">
    Препарат {{count}}
  </button>
</template>
<script>
export default {

  data() {
    return {
      styles: {
        color: 'white',
        backgroundColor: this.color,
        border: '1px solid red',
      },
    };
  },
  props: {
    count: Number,
    color: String,
    sadClicks: Number,
    value: Number,
  },
  computed: {
    classObject() {
      return {
        Rectangle: true,
        yellow: this.color === 'yellow',
        blue: this.color === 'blue',
        purple: this.color === 'purple',
      };
    },
  },
  methods: {
    log() {
      console.log(this.color);
    },
  },
};
</script>

<style lang="scss" rel="stylesheet/scss">
  @import'./component-styles/rectangleButton.scss';
</style>
