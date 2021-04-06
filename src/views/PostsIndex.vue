<template>
  <div class="posts-index">
    <h1>{{ message }}</h1>
    <div v-for="post in posts" v-bind:key="post.id">
      <router-link v-bind:to="`/posts/${post.id}`">{{ post.title }}</router-link>

      <hr />
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to the Posts Page!",
      posts: [],
    };
  },
  created: function () {
    this.postsIndex();
  },
  methods: {
    postsIndex: function () {
      console.log("index");
      axios.get("/api/posts/").then((response) => {
        console.log(response.data);
        this.posts = response.data;
      });
    },
  },
};
</script>
