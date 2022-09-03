<template>
  <button title="Search">
    <slot></slot>
  </button>
</template>
<script setup></script>
<style scoped>
button {
  background-color: #4caf4fc3;
  border: none;
  color: white;
  padding: 10px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  transition: all 0.3s ease;
  outline: none;
}
button:hover {
  background-color: #3e8e41;
  transform: scale(1.05);
}
</style>
