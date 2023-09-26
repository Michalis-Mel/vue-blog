<template>
  <div class="addArticle">
    <CreatePostForm />
    <button class="back" @click="goBack">Go Back</button>
  </div>
</template>

<script>
import CreatePostForm from "@/components/CreatePostForm.vue";
export default {
  components: { CreatePostForm },
  methods: {
    goBack() {
      this.$router.go(-1);
    },
  },
};
</script>

<style></style>
