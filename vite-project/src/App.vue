<script>
import Modal from "./components/Modal.vue";
import { ref } from "vue";
// Reactive reference ref Composition API
// const msg = ref("Hello Vite");
export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "Hello Vite",
      // header: "This is a header from data",
      // text: "Grab the content from data",
      // theme: "light",
      showModal: false,
      showModal2: false,
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2;
    },
  },
};
</script>

<template>
  <div>
    <h1>{{ title }}</h1>
    <div v-if="showModal">
      <!-- slot -->
      <Modal theme="sale" @close="toggleModal">
        <h1>Mehedi using slot</h1>
        <p>Content for madal</p>
        <template v-slot:link>
          <a href="https://www.google.com">Google</a>
        </template>
      </Modal>
      <!-- <Modal :header="header" :text="text" theme="sale" @close="toggleModal" /> -->
    </div>
    <div v-if="showModal2">
      <!-- slot -->
      <Modal theme="salee" @close="toggleModal2">
        <h1 class="headerTitle">Second Modal using click evet</h1>
        <p>Content for madal</p>
        <template v-slot:link>
          <a href="https://www.google.com">Google</a>
        </template>
      </Modal>
      <!-- <Modal :header="header" :text="text" theme="sale" @close="toggleModal" /> -->
    </div>
    <button @click.alt="toggleModal">Toggle Modal(alt+click)</button>
    <button @click="toggleModal2">Second Modal</button>
  </div>
</template>

<style scoped>
h1 {
  color: rgb(27, 134, 95);
  font-size: 2rem;
}
p {
  color: rgb(51, 51, 51);
}
</style>
