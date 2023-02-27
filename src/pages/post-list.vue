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
    <v-card
      v-for="post in posts"
      :key="post.id"
      class="mx-auto my-4"
      max-width="344"
      variant="outlined"
      :style="{backgroundColor: '#336D95'}"
    >
      <v-card-item>
        <div class="text-overline mb-1">ユーザー名</div>
        <div class="mb-1">ユーザーID</div>
        <div class="text-bold text-caption">
          {{ post.content }}
        </div>
        <div>タグ</div>
      </v-card-item>

      <v-card-actions>
        <v-btn icon="mdi-comment" variant="text" color="white"></v-btn>
        <v-btn icon="mdi-thumb-up" variant="text" color="white"></v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<style scoped lang="scss">
@import "../assets/css/variable.scss";

.post-list-page {
  background-color: $main-backgrond-color;
  height: 100vh;
  padding: 16px 0;
}
</style>
