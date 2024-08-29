<template>
  <div class="block" v-if="showBloack" @click="stopTimer">
    <h3>Click me</h3>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBloack: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    console.log("mounted");
    setTimeout(() => {
      this.showBloack = true;
      // console.log(this.delay);
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.showBloack = true;
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime);
      this.$emit("end", this.reactionTime);
    },

    // handleClick() {
    //   this.showBloack = false;
    //   this.$emit("block-clicked");
    // },
  },
};
</script>

<style>
.block {
  width: 400px;
  background-color: rgb(10, 92, 125);
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 24px;
  color: white;
  border-radius: 1.4rem;
  padding: 8rem 0;
  margin: 40px auto;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  cursor: pointer;
}
</style>
