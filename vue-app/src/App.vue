<template>
  <Fallback/>

  <div id="main">

    <WelcomeScreen
      v-if="isStarted && !isEnd"
      v-model="isStarted"
    />
    <!--    Main screen-->
    <div class="wrapper" v-if="!isStarted && !isEnd">
      <div class="side-wrapper sidebar">
        <div class="box nav-container">
          <button class="roundButton-home" @click="goStart"></button>
          <button class="roundButton-reset" @click="reset"></button>
        </div>
        <div>
          <div>
            <p class="pill-header">Параметри:</p>
          </div>
          <div class="box pill-container">
            <Pill :image="getImage('sad', 'svg')" :count="sadClicks"/>
            <Pill :image="getImage('happy', 'svg')" :count="happyClicks"/>
            <Pill :image="getImage('love', 'svg')" :count="loveClicks"/>
          </div>
        </div>
        <div class="box counter-container">
          <Counter :current="currentStep+1" :total="totalSteps"/>
        </div>
      </div>
      <div class="box content">
        <div class="container-wrapper">
          <div class="container-content">
            <Card :image="getImage()" :title="getTitle()" :text="getDescription()"/>
          </div>
          <div class="buttons-bottom">
            <RectangleButton
              count="1"
              @click="increaseSad" :value="sadClicks" v-model="sadClicks" color="purple"/>
            <RectangleButton
              count="2"
              @click="increaseHappy" :value="happyClicks" v-model="happyClicks" color="blue"/>
            <RectangleButton
              count="3"
              @click="increaseLove" :value="loveClicks" v-model="loveClicks" color="yellow"/>
          </div>
        </div>
      </div>
    </div>

    <ResultScreen
      v-if="isEnd"
      v-model="isEnd"
      :happy="computePercents('happyClicks')"
      :love="computePercents('loveClicks')"
      :sad="computePercents('sadClicks')"
      @restartGame="goStart"
    />
  </div>
</template>

<script>
import RectangleButton from './components/RectangleButton.vue';
import Pill from './components/Pill.vue';
import Card from './components/Card.vue';
import Counter from './components/Counter.vue';
import WelcomeScreen from './components/WelcomeScreen.vue';
import ResultScreen from './components/ResultScreen.vue';
import Fallback from './components/Fallback.vue';
import PERSONAS from './utils/constants';

export default {
  name: 'App',
  el: '#app',
  components: {
    Pill,
    RectangleButton,
    Card,
    Counter,
    WelcomeScreen,
    ResultScreen,
    Fallback,
  },
  data() {
    return {
      isStarted: true,
      isEnd: false,

      sadClicks: 0,
      happyClicks: 0,
      loveClicks: 0,

      currentStep: 0,
      totalSteps: PERSONAS.length,
    };
  },
  methods: {
    getImage(name, extension) {
      // eslint-disable-next-line global-require,import/no-dynamic-require
      return require(`./assets/${name || this.currentStep}.${extension || 'png'}`);
    },
    getDescription() {
      return PERSONAS[this.currentStep].description;
    },
    getTitle() {
      return PERSONAS[this.currentStep].title;
    },
    showEndGame() {
      this.isEnd = true;
      this.isStarted = true;
    },
    increaseStep() {
      this.currentStep += 1;
      if (this.currentStep >= this.totalSteps) {
        this.showEndGame();
      }
    },
    increaseSad() {
      this.increaseStep();
      this.sadClicks += 1;
    },
    increaseHappy() {
      this.increaseStep();
      this.happyClicks += 1;
    },
    increaseLove() {
      this.increaseStep();
      this.loveClicks += 1;
    },
    reset() {
      this.sadClicks = 0;
      this.happyClicks = 0;
      this.loveClicks = 0;
      this.currentStep = 0;
    },
    goStart() {
      this.isStarted = true;
      this.isEnd = false;

      this.sadClicks = 0;
      this.happyClicks = 0;
      this.loveClicks = 0;

      this.currentStep = 0;
      this.totalSteps = PERSONAS.length;
    },
    computePercents(value) {
      return Math.round((this[value] / this.totalSteps) * 100);
    },
  },
};
</script>

<style lang="scss" rel="stylesheet/scss">
@import './normalize.scss';
@import './fonts.scss';
@import './app.scss';
</style>
