<script setup lang="ts">
import { API_BASE_URL } from "../config/index.ts";
definePageMeta({
  layout: "header",
});

const { data: posts } = await useFetch(`${API_BASE_URL}/posts`, {
  method: "GET",
});
console.log({ posts });
</script>

<template>
  <div class="post-list-page">
    <ul>
      <li v-for="post in posts" :key="post.id">{{ post.content }}</li>
    </ul>
  </div>
</template>

<style scoped lang="scss">
@import "../assets/css/variable.scss";

.post-list-page {
  background-color: $main-backgrond-color;
  height: 100vh;
}
</style>
