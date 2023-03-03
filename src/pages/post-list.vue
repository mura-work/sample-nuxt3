<script setup lang="ts">
import { API_BASE_URL } from "../config/index.ts";
definePageMeta({
  layout: "header",
});

const { data: posts } = await useFetch(`${API_BASE_URL}/posts`, {
  method: "GET",
});
console.log({ posts });

const openPostModal = useState("openPostModal", () => false);
const toggleModal = (value) => {
  openPostModal.value = value;
};

// const postContent = useState("postContent", () => "")
const postContent = ref("");
const savePostForm = (e) => {
  console.log({ e, postContent });
  toggleModal(false);
};
</script>

<template>
  <div class="post-list-page">
    <v-card
      v-for="post in posts"
      :key="post.id"
      class="mx-auto my-4"
      max-width="344"
      variant="outlined"
      :style="{ backgroundColor: '#336D95' }"
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
    <v-btn
      @click="toggleModal(true)"
      class="!absolute bottom-0 right-4"
      size="x-large"
      variant="text"
      color="white"
      icon
    >
      <v-icon size="x-large">mdi-plus-circle</v-icon>
    </v-btn>
  </div>

  <v-dialog v-model="openPostModal" persistent width="1024">
    <v-card>
      <v-card-item>
        <v-textarea
          placeholder="投稿内容を入力"
          :modelValue="postContent"
          @update:modelValue="postContent = $event"
          rows="10"
          required
        ></v-textarea>
      </v-card-item>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="blue-darken-1" variant="text" @click="toggleModal(false)">
          キャンセル
        </v-btn>
        <v-btn color="blue-darken-1" variant="text" @click="savePostForm">
          投稿
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<style scoped lang="scss">
@import "../assets/css/variable.scss";

.post-list-page {
  background-color: $main-backgrond-color;
  height: 100vh;
  padding: 16px 0;
}
</style>
