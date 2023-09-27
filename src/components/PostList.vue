<template>
  <div class="post-list">
    <div
      v-for="post in posts.slice().reverse()"
      :key="post.id"
      class="post_con"
    >
      <SinglePost :post="post" />
    </div>
  </div>
</template>

<script>
import SinglePost from "@/components/SinglePost.vue";
export default {
  props: ["posts"],
  components: { SinglePost },
};
</script>
