<template>
  <main>
    <VInputForm v-model="url" @search="load()" />

    <VTable
      :table="data"
      :url="searchUrl"
      v-if="data.length > 0"
      @onEnd="loadMore()"
    />

    <VMessage :message="message" />
  </main>
</template>
<script setup>
import VInputForm from "@/components/infitity-scroll/v-input-form.vue";
import VTable from "@/components/infitity-scroll/v-table.vue";
import axios from "axios";
import { ref } from "vue";
import VMessage from "./components/UI/v-message.vue";

const data = ref([]);
const limit = ref(10);
const page = ref(1);
const url = ref("https://jsonplaceholder.typicode.com/posts");
const searchUrl = ref("");
const message = ref({ show: false });

function load() {
  page.value = 1;
  axios
    .get(url.value, {
      params: {
        _limit: limit.value,
        _page: page.value,
      },
    })
    .then((res) => {
      if (res.status == 200) {
        data.value = res.data;
        searchUrl.value = url.value;
      }
    })
    .catch((err) => {
      message.value = { show: true, title: "Error", body: err.message };
    });
}

function loadMore() {
  page.value += 1;
  axios
    .get(searchUrl.value, {
      params: {
        _page: page.value,
        _limit: limit.value,
      },
    })
    .then((response) => {
      data.value = [...data.value, ...response.data];
    })
    .catch((error) => {
      console.log(error);
    });
}
</script>

<style scoped>
main {
  min-height: 100vh;
  max-width: 1200px;
  padding: 3rem;
  margin: 0 auto;
}
@media (max-width: 1000px) {
  main {
    padding: 1rem;
  }
}
</style>
