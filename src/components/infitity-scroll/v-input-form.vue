<template>
  <div class="main-form">
    <section>
      <VInput
        v-model="modelValue"
        @input="emits('update:modelValue', $event.target.value)"
      />
      <VButton @click="emits('search')" class="btn">Search</VButton>
    </section>
    <VExample @onClick="emits('update:modelValue', $event)" />
  </div>
</template>
<script setup>
import VInput from "../UI/v-input.vue";
import VButton from "../UI/v-button.vue";
import VExample from "./v-example.vue";

const props = defineProps(["modelValue"]);
const emits = defineEmits(["update:modelValue", "search"]);
</script>
<style scoped>
section {
  display: flex;
  align-items: center;
}
.main-form {
  width: 500px;
  margin: 0 auto;
  transition: all 0.3s ease;
}
.btn {
  margin-left: 10px;
}

@media (max-width: 600px) {
  .main-form {
    width: 100%;
  }
  section {
    flex-direction: column;
  }
}
</style>
