<template>
  <div class="posts-show">
    <h1>{{ message }}</h1>
    <p>Id: {{ post.id }}</p>
    <p>Title: {{ post.title }}</p>
    <p>Body: {{ post.body }}</p>
    <p>Image: {{ post.image }}</p>
    <router-link v-bind:to="`/posts/${this.$route.params.id}/edit`">Edit Post</router-link>
    <p>
      <button v-on:click="PostsDelete()">Delete Post</button>
    </p>
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
  methods: {
    PostsDelete: function () {
      axios.delete(`/api/posts/${this.$route.params.id}`).then((response) => {
        console.log(response.data);
        this.$router.push("/posts");
      });
    },
  },
};
</script>
