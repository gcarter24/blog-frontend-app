<template>
  <div class="posts-show">
    <h1>{{ message }}</h1>
    <p>Id: {{ post.id }}</p>
    <p>Title: {{ post.title }}</p>
    <p>Body: {{ post.body }}</p>
    <p>Image: {{ post.image }}</p>
    <p>User:</p>
  </div>
</template>

<style></style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to the Show Page!",
      post: {},
    };
  },
  created: function () {
    console.log(this.$route.params.id);
    axios.get(`/api/posts/${this.$route.params.id}`).then((response) => {
      console.log(response.data);
      this.post = response.data;
    });
  },
  methods: {},
};
</script>
