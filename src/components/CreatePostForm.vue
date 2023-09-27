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
      <input type="text" v-model="post.tempTag" @keyup="addTag" />
      <div class="tags">
        <div
          v-for="tag in post.tags"
          :key="tag"
          class="tag"
          @click="deleteTag(tag)"
        >
          {{ tag }}
        </div>
      </div>

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
        tempTag: "",
        tags: [],
      },
      submited: false,
      submitedText: false,
    };
  },
  methods: {
    addTag(e) {
      if ((e.key === "," || e.key === " ") && this.post.tempTag) {
        if (!this.post.tags.includes(this.post.tempTag)) {
          this.post.tags.push(this.post.tempTag);
        }
        this.post.tempTag = "";
      }
    },
    deleteTag(tag) {
      this.post.tags = this.post.tags.filter((item) => tag !== item);
    },
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
