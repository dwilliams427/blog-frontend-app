<template>
  <div class="posts-show">
    <div class="container">
      <h1>{{ post.title }}</h1>
      <img v-bind:src="post.image" v-bind:alt="post.title" />
      <p>{{ post.body }}</p>
      <router-link v-bind:to="`/posts/${post.id}/edit`">Edit Post</router-link>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      post: {},
    };
  },
  created: function () {
    this.showPost();
  },
  methods: {
    showPost: function () {
      axios.get("/api/posts/" + this.$route.params.id).then((response) => {
        console.log("showing post", response);
        this.post = response.data;
      });
    },
  },
};
</script>
