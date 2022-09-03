<template>
  <div class="observe" ref="observe" />
</template>
<script setup>
import { onMounted, ref } from "vue";

const observe = ref(null);
const emits = defineEmits(["observe"]);
onMounted(() => {
  var options = {
    rootMargin: "0px 0px 100px 0px",
    threshold: 1.0,
  };
  var callback = function (entries) {
    entries[0].isIntersecting ? emits("observe") : null;
  };
  var observer = new IntersectionObserver(callback, options);
  observer.observe(observe.value);
});
</script>
<style scoped></style>
