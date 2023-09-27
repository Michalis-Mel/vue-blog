<template>
  <h1>Create Post</h1>
  <div v-if="submited">
    <div v-if="submitedText" class="success">
      <h4>Your Post is created!</h4>
    </div>
    <div v-else class="failed">
      <h4>There was an error creating your post...</h4>
    </div>
  </div>
  <div v-else style="width: 100%">
    <form @submit.prevent="handleSubmit">
      <label>Title: </label>
      <input v-model="post.title" type="text" required />
      <label>Body: </label>
      <input v-model="post.body" type="text" required />
      <label>Tags: </label>
      <input v-model="post.tags" type="text" />
      <button class="create">Create Post</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      post: {
        title: "",
        body: "",
        tags: "",
      },
      submited: false,
      submitedText: false,
    };
  },
  methods: {
    handleSubmit() {
      axios.post("http://localhost:3000/posts", this.post).then((res) => {
        console.log(res);
      });
      this.submited = true;
      this.submitedText = true;
    },
  },
};
</script>
