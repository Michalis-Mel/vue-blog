<template>
  <div class="notFound">
    <div class="row">
      <h2>404</h2>
      <h2>Page not found!</h2>
      <button class="back" @click="goBack">Go Back</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    goBack() {
      this.$router.go(-1);
    },
  },
};
</script>
