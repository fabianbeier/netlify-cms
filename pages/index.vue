<template>
  <div class="container">
    <li v-for="post of posts" :key="post.slug">
      <NuxtLink :to="post.slug">{{ post.title }}</NuxtLink>
      <p>{{post.description}}</p>
    </li>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const posts = await $content("recipes").fetch();

    return {
      posts,
    };
  },
};
</script>

<style>

</style>
