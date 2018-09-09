<template>
  <div id="app">
    <h1>Reddit Client</h1>
    <div class="post-list">
      <div v-for="(p, index) in posts" :key="p.id" class="post-wrapper">
        <h3>Post {{ index + 1 }}:</h3>
        <post :data="p" />
      </div>
    </div>
  </div>
</template>

<script>
import mockPosts from "./mock.json";
import Post from "@/components/Post.vue";
import { getPosts } from "@/services/reddit.service.js";

export default {
  name: "app",
  data: function() {
    return { posts: mockPosts };
  },
  components: {
    Post
  },
  mounted: function() {
    getPosts().then(newPosts => {
      this.posts = newPosts;
    });
  }
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css?family=Pragati+Narrow");

body {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.post-list {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;

  font-family: "Pragati Narrow";

  .post-wrapper {
    width: 65%;
    min-width: 300px;
  }
}

h1 {
  font-family: "Pragati Narrow";
  text-align: center;
  font-size: 100px;
  margin-bottom: 0px;
}
</style>
