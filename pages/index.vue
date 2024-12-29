<script setup lang="ts">
import { getPostsUrl, type Post } from "~/data/posts";

const { data: posts } = await useFetch<Post[]>(getPostsUrl());
</script>

<template>
  <main>
    <h1>Nuxt.js Exampled</h1>
    <div>
      <PostCard v-for="post in posts" :key="post.id" :post="post"/>
    </div>
  </main>
</template>
