<template>
  <div class="home">
    <div class="row">
      <h1>Home</h1>
      <div v-if="error">{{ error }}</div>
      <div v-else style="width: 100%">
        <div v-if="posts.length" style="width: 100%">
          <PostList :posts="posts" />
        </div>
        <div v-else>Loading...</div>
      </div>
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
