<template>
  <div class="container flex max-w-screen-lg">
    <li v-for="post of posts" :key="post.slug" class="text-2xl text-white list-none shadow-lg m-6 p-4 bg-pink-400 duration-200 hover:bg-pink-800 w-1/3">
      <NuxtLink :to="post.slug">{{ post.title }}</NuxtLink>
      <p class="text-base">{{post.description}}</p>
    </li>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const posts = await $content("recipes").sortBy('title').fetch();

    return {
      posts,
    };
  },
};
</script>

<style>

</style>
