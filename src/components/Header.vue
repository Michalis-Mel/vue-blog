<template>
  <header>
    <div class="row">
      <router-link to="/" class="logo">
        <img src="@/assets/logo-small.png" alt="Logo" /> M² BLOG
      </router-link>
      <nav>
        <router-link to="/"> Home </router-link>
        <router-link :to="{ name: 'addPost' }">Create Post</router-link>
      </nav>
    </div>
  </header>
</template>

<script>
export default {};
</script>
