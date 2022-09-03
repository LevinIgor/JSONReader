<template>
  <h2>{{ url }}</h2>
  <table>
    <thead>
      <tr>
        <th v-for="header in headers()" :key="header.text">
          {{ header }}
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in table" :key="item.id">
        <td v-for="field in item" :key="field">
          {{ field }}
        </td>
      </tr>
    </tbody>
  </table>
  <VObserver @observe="emits('onEnd')" />
</template>
<script setup>
import VObserver from "./v-observer.vue";

const props = defineProps(["table", "url"]);
const emits = defineEmits(["onEnd"]);

const headers = () => {
  return Object.keys(props.table[0]);
};
</script>
<style scoped>
h2 {
  text-align: center;
  margin: 100px 0 10px 0;
  font-size: 16px;
  font-family: "Times New Roman", Times, serif;
}
table {
  margin: 0 auto;
  user-select: none;
  cursor: default;
  width: 100%;
  overflow-x: scroll;
}
thead tr {
  position: sticky;
  top: 0;
  z-index: 10;
}
th {
  font-size: clamp(12px, 1vw, 18px);
  font-weight: 500;
  text-align: center;
  text-transform: uppercase;
  border: 1px solid #e0e0e0;
  padding: 5px 10px;
  background-color: rgb(45, 45, 45);
  opacity: 1;
  z-index: 10;
  color: #e0e0e0;
}
td {
  padding: 10px;
  font-size: clamp(10px, 1vw, 18px);
  text-align: center;
  border: 1px solid #e0e0e0;
}
tbody tr:nth-child(odd) {
  background-color: #e4e4e44c;
}

tbody tr:nth-child(even) {
  background-color: #8888883a;
}
@media (max-width: 600px) {
  th {
    padding: 0 5px;
  }
  td {
    padding: 0 5px;
  }
}
.fade-enter-active,
.fade-leave-active {
  transition: all 0.4s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
