<template>
  <div>
    <!-- <h3>Results</h3> -->
    <p>Reaction Time: {{ score }}ms</p>
    <p class="rank">{{ rank }}</p>
    <button @click="restartGame">Restart</button>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 200) {
      this.rank = "Excellent! You are a Champ!";
    } else if (this.score < 250) {
      this.rank = "Pro Gamer";
    } else if (this.score < 300) {
      this.rank = "Rapid Reflexes";
    } else {
      this.rank = "Snal pace...";
    }
  },
  methods: {
    restartGame() {
      this.$emit("restart");
      this.rank = null;
    },
  },
};
</script>

<style>
.rank {
  font-size: 24px;
  font-weight: 700;
  color: rgb(10, 202, 67);
}
</style>
