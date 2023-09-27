<template>
  <div class="post">
    <router-link :to="{ name: 'details', params: { id: post.id } }">
      <h3>{{ post.title }}</h3>
    </router-link>
    <p>{{ snippet }}</p>
    <div class="tags">
      <span v-for="tag in post.tags" :key="tag"> #{{ tag }}</span>
    </div>

    <button @click="deletePost">Delete Post</button>
  </div>
</template>

<script>
import axios from "axios";
import { computed } from "vue";

export default {
  props: ["post"],
  setup(props) {
    const snippet = computed(() => {
      return props.post.body.substring(0, 100) + "...";
    });

    return { snippet };
  },
  methods: {
    deletePost() {
      axios
        .delete(`http://localhost:3000/posts/${this.post.id}`)
        .then((res) => {
          console.log(res);
        });
      this.$router.go(this.$router.currentRoute);
    },
  },
};
</script>
