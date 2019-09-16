<template>
  <section class="section">
    <div class="container">
      <div class="columns">
        <div class="column is-offset-2 is-8">
          <h2 class="title is-2">Latest Post</h2>
          <hr />
          <h2 class="title is-4" v-for="(post, index) in posts" :key="index">
            <nuxt-link :to="post.fields.slug">{{post.fields.title}}</nuxt-link>
          </h2>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import client from "~/plugins/contentful";
export default {
  asyncData() {
    return client
      .getEntries({
        content_type: "post"
      })
      .then(entries => {
        return { posts: entries.items };
      })
      .catch(err => console.log(err));
  },
  head: {
    title: "Noobita | Web Developer, VueJS, Django, Python"
  }
};
</script>

<style>
</style>

