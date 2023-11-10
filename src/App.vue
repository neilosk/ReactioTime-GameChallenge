<template>
  <h1>I want to play a game</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <BoxV v-if:="isPlaying" :delay="delay" @stop="stopGame" />
  <ResultsV v-if="showResult" :score="score" />
</template>

<script>
import BoxV from "./components/BoxV.vue";
import ResultsV from "./components/ResultsV.vue";

export default {
  name: "App",
  components: { BoxV, ResultsV },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult = false;
    },
    stopGame(reactionTime) {
      this.isPlaying = false;
      this.score = reactionTime;
      this.showResult = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #f4eded;
  margin-top: 60px;
}
button {
  border: 2px solid #f4eded;
  border-radius: 5px;
  background-color: #f4eded;
  color: #000000;
  size: 100px;
  padding: 10px 20px;
  font-size: 20px;
  font-weight: bold;
}

button[disabled] {
  background-color: #4e4d4d;
  color: #000000;
  opacity: 0.5;
}
</style>
