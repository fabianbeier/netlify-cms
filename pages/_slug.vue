<template>
    <div>
    <h2>{{ post.title }}</h2>
    <h2 class="bg-teal-300 ">{{ post.description }}</h2>
    <nuxt-content :document="post" />
    <li v-for="section in post.sections">{{section.section}}</li>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let post;
    try {
      post = await $content("recipes", params.slug).fetch();
      // OR const article = await $content(`articles/${params.slug}`).fetch()
    } catch (e) {
      error({ message: "Blog Post not found" });
    }

    return {
      post,
    };
  },
};
</script>

<style>

</style>