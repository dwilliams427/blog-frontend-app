<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/about">About</router-link>
      |
      <router-link to="/test">Test</router-link>
      |
      <router-link to="/signup">Signup</router-link>
      |
      <router-link to="/login">Login</router-link>
      |
      <router-link to="/logout">Logout</router-link>
      |
      <router-link to="/index">All Posts</router-link>
      |
      <router-link to="/posts/new">Create A Post</router-link>
      <!-- |
      <router-link to="/posts/:id"></router-link> -->
    </div>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand" href="#">Bloggo</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item active">
            <a class="nav-link" href="#">
              <router-link to="/" class="nav-link">
                Home
                <span class="sr-only">(current)</span>
              </router-link>
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">All Posts</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Create Post</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#" tabindex="-1">Sign Up</a>
          </li>
        </ul>
      </div>
    </nav>
    <router-view />
  </div>
</template>
<style>
#app {
  font-family: Avant Garde, Avantgarde, Century Gothic, CenturyGothic, AppleGothic, sans-serif;
  background-image: url("./assets/double-bubble-outline.png");
}
</style>
