<template>
  <div v-if="message.show">
    <h2>{{ message.title }}</h2>
    <p>{{ message.body }}</p>
  </div>
</template>
<script setup>
import { watch } from "vue";
const props = defineProps(["message"]);

// Disable visible message, when timer is over (3000ms)
watch(
  () => props.message,
  (val) => {
    if (val.show) {
      setTimeout(() => {
        props.message.show = false;
      }, 3000);
    }
  }
);
</script>
<style scoped>
div {
  box-sizing: border-box;
  position: fixed;
  top: 10px;
  left: 50%;
  transform: translateX(-50%);
  background-color: rgb(255, 255, 255);
  border: 1px solid rgba(0, 0, 0, 0.21);
  border-radius: 5px;
  padding: 20px 40px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  z-index: 1000;
}
h2,
p {
  text-align: center;
  color: rgb(23, 23, 23);
}
</style>
