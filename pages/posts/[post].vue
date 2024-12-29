<script setup lang="ts">
import type { PostDetails } from "~/data/posts";
import { getPostDetailsUrl } from "~/data/posts";
import { useParam } from "~/composables/useParam";

definePageMeta({
    layout: 'breadcrumb'
})

const postSlug = useParam('post')

const { data: post } = await useFetch<PostDetails>(getPostDetailsUrl(postSlug));

const categoryState = useState('category', () => ({
    name: "",
    slug: ""
}))

if (post.value) {
    categoryState.value = {
        name: post.value?.category.name,
        slug: post.value?.category.slug
    }
}

</script>

<template>
    <main>
        <template v-if="post">
            <h1>{{ post.title }}
                <CategoryLink :category="post?.category" />
            </h1>

            <RenderMarkdown :source="post?.content" />
        </template>
    </main>
</template>
