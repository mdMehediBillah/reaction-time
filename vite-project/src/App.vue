<template>
  <div>
    <h1>Reaction Time Calculation</h1>
    <button class="btnStart" @click="startGame" :disabled="isPlaying">
      Start Game
    </button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <Results v-if="showResults" :score="score" @restart="handleRestart" />
    <!-- <p v-if="showResults">Reaction Time: {{ score }}ms</p> -->
  </div>
</template>

<!-- script -->
<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    startGame() {
      this.showResults = false;
      this.delay = Math.floor(Math.random() * 5000) + 2000;
      this.isPlaying = true;
      // console.log(this.delay);
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
      console.log(reactionTime);
    },
    handleRestart() {
      this.showResults = false;
      this.score = 0; // Reset the score or handle other restart logic
    },
  },
};
</script>

<style scoped>
.btnStart {
  padding: 0.5rem 1rem;
  font-size: 1.2rem;
  background-color: rgb(4, 125, 97);
  color: rgb(254, 255, 213);
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
}
.btnStart:disabled {
  background-color: rgb(200, 200, 200);
  cursor: not-allowed;
}
.btnStart:hover {
  background-color: rgb(4, 125, 77);
  scale: 1.1;
  transition: all 0.3s ease;
}
</style>
