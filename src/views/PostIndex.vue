<template>
  <div class="posts-index">
    <div>
      <div v-for="post in posts" v-bind:key="post.id">
        <h3>{{ post.title }}</h3>
        <img v-bind:src="post.image" v-bind:alt="post.title" />
        <p>{{ post.body }}</p>
        <router-link v-bind:to="`/posts/${post.id}`">More Details</router-link>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      posts: [],
    };
  },
  created: function () {
    this.indexPosts();
  },
  methods: {
    indexPosts: function () {
      axios.get("/api/posts").then((response) => {
        console.log("posts index", response);
        this.posts = response.data;
      });
    },
  },
};
</script>
