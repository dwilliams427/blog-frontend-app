<template>
  <div class="posts-edit">
    <form v-on:submit.prevent="editPost(post)">
      <h1>Edit Post</h1>
      <ul>
        <li class="text-danger" v-for="error in errors" v-bind:key="error">
          {{ error }}
        </li>
      </ul>
      <div class="form-group">
        <label>Title:</label>
        <input type="text" class="form-control" v-model="post.title" />
      </div>
      <div class="form-group">
        <label>Body:</label>
        <input type="text" class="form-control" v-model="post.body" />
      </div>
      <input type="submit" class="btn btn-primary" value="Submit" />
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      post: {},
      errors: [],
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
        .then(() => {
          console.log("editing post");
          this.$router.push("/posts/" + this.recipe.id);
        })
        .catch((error) => {
          console.log("error" + error.response);
        });
    },
  },
};
</script>
