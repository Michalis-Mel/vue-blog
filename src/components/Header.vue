<template>
  <div class="row">
    <router-link to="/" class="logo">
      <img src="@/assets/logo-small.png" alt="Logo" /> M² BLOG
    </router-link>
    <router-link :to="{ name: 'addPost' }" class="create_link"
      >Create New Post</router-link
    >
  </div>
</template>

<script>
export default {};
</script>

<style></style>
