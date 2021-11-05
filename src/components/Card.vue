<template>
  <div class="card">
    <h4>{{ post.title }}</h4>
    <h5>{{ post.body }}</h5>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    post: Object,
    title: String,
  },
};
</script>

<style scoped>
.card {
  height: 200px;
  background-color: rgb(192, 132, 132);
}
</style>
