<template>
  <input
    type="text"
    :value="props.modelValue"
    @input="emits('update:modelValue', $event.target.value)"
  />
</template>
<script setup>
const props = defineProps(["modelValue"]);
const emits = defineEmits(["update:modelValue"]);
</script>
<style scoped>
input {
  width: 100%;
  padding: 10px 20px;
  margin: 8px 0;
  box-sizing: border-box;
  border: 1px solid #ccc;
  -webkit-transition: 0.5s;
  transition: 0.5s;
  outline: none;
  font-size: 16px;
}
</style>
