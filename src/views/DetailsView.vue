<template>
  <div class="details">
    <div class="row">
      <h1>Details</h1>
      <div v-if="error" class="error">{{ error }}</div>
      <div v-else>
        <div v-if="post" class="postDetails">
          <h3>{{ post.title }}</h3>
          <p>{{ post.body }}</p>
        </div>
        <div v-else class="loading">Loading...</div>
      </div>
      <button class="back" @click="goBack">Go Back</button>
    </div>
  </div>
</template>

<script>
import getPost from "@/composables/getPost";
export default {
  props: ["id"],
  setup(props) {
    const { post, error, load } = getPost(props.id);
    load();

    return { post, error };
  },
  methods: {
    goBack() {
      this.$router.go(-1);
    },
  },
};
</script>
