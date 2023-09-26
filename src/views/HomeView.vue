<template>
  <div class="home">
    <h1>Home</h1>
    <router-link :to="{ name: 'addPost' }">Create New Post</router-link>
    <div v-if="error">{{ error }}</div>
    <div v-else>
      <div v-if="posts.length">
        <PostList :posts="posts" />
      </div>
      <div v-else>Loading...</div>
    </div>
  </div>
</template>

<script>
import PostList from "@/components/PostList.vue";
import getPosts from "@/composables/getPosts";

export default {
  name: "HomeView",
  components: { PostList },
  setup() {
    const { posts, error, load } = getPosts();
    load();
    return { posts, error };
  },
};
</script>
