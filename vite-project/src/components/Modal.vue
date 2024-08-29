<script>
export default {
  props: ["header", "text", "theme"],
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>

<!-- template -->
<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <slot>default Content</slot>
      <div>
        <slot name="link"></slot>
      </div>
      <!-- <h1>{{ header }}</h1>
      <p>{{ text }}</p> -->
    </div>
  </div>
</template>

<!-- style -->
<style scoped>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}
h1 {
  color: rgb(36, 36, 121);
  font-size: 2rem;
}
p {
  color: rgb(51, 51, 51);
}
.sale {
  background: cyan;
}
</style>
