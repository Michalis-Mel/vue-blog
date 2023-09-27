<template>
  <div class="addPost">
    <div class="row">
      <CreatePostForm />
      <button class="back" @click="goBack">Go Back</button>
    </div>
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
