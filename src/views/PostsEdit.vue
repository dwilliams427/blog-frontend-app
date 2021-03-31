<template>
  <div class="posts-edit">
    <div class="container">
      <h1>Edit Post</h1>
      <form v-on:submit.prevent="editPost(post)">
        <ul>
          <li v-for="error in errors" v-bind:key="error">{{ errors }}</li>
        </ul>
        <label>Title:</label>

        <input type="text" v-model="post.title" />
        Body:
        <input type="text" v-model="post.body" />
        <!-- Image:
        <input type="text" v-model="post.image" /> -->
        <button v-on:click="editPost(post)">Update</button>
      </form>
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
    axios.get("/api/posts/" + this.$route.params.id).then((response) => {
      console.log("showing post", response);
      this.post = response.data;
    });
  },
  methods: {
    editPost: function (post) {
      var params = {
        title: post.title,
        body: post.body,
        image: post.image,
      };
      axios
        .patch("/api/posts/" + this.$route.params.id, params)
        .then((response) => {
          console.log("editing post", response);
          this.$router.push("/posts/" + this.recipe.id);
        })
        .catch((error) => {
          console.log("error" + error.response);
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>
