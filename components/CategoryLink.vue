<script setup lang="ts">
import type { Category } from "~/data/categories";

const { category } = defineProps<{ category: Category }>();
</script>

<template>
  <div class="category">
    <NuxtLink :to="`/categories/${category.slug}`">Category: {{ category.name }}</NuxtLink>
  </div>
</template>

<style scoped lang="scss">
@use "@/assets/styles/colors.scss";

.category {
  display: block;
  margin: 15px 0px;

  a {
    color: colors.$green-medium;
    font-size: 12pt;
    border: 1px solid colors.$green-dark;
    border-radius: 5px;
    padding: 5px 10px;
  }

  a:hover {
    color: colors.$green-light;
    background-color: colors.$green-medium;
  }
}
</style>
