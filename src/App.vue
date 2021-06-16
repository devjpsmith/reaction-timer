<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <block v-if="isPlaying" :delay="delay" @blockClick="handleClick"/>
  <results v-if="showResults" :score="score" />
</template>

<script>
import Block from './components/block.vue'
import Results from './components/results.vue';

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data() {
    return {
      delay: null,
      score: 0,
      isPlaying: false,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 0 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    handleClick(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button {
  background: #0faf87;
  color: #fff;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
