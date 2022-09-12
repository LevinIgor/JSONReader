<template>
  <article>
    <div class="example">Examples</div>
    <div class="example__link">
      <span
        v-for="(link, index) in links"
        :key="index"
        @click="emits('onClick', link.url)"
      >
        {{ link.text }}</span
      >
    </div>
  </article>
</template>
<script setup>
import links from "@/JSON/links.json";
const emits = defineEmits(["onClick"]);
</script>
<style scoped>
article {
  display: flex;
  align-items: center;
}
.example__link {
  user-select: none;
  margin-left: 10px;
  display: flex;
  align-items: center;
  width: 100%;
}
.example {
  font-weight: 600;
  font-size: 12px;
}
span {
  margin: 5px 5px;
  padding: 0 10px;
  font-size: 10px;
  text-decoration: underline;
  cursor: pointer;
}
@media (max-width: 600px) {
  article{
    display: block;
    text-align: center;
  }
  .example__link {
    display: grid;
    grid-template-columns: 1fr 1fr;
    margin: 0;
  }
  span {
    margin: 5px 0;
  }
}
</style>
