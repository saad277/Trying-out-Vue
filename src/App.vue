<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <p v-if="score" >Reaction time {{score}} ms</p>
</template>

<script>
import { Block } from "./components/Block";

export default {
  name: "App",
  components: { Block },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
    };
  },

  methods: {
    start() {
      this.delay = 2000;
      this.isPlaying = true;
    },
    endGame(val) {
      this.score = val;
      this.isPlaying=false
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
  color: #444;
  margin-top: 60px;
}
</style>
