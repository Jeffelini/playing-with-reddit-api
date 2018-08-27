<template>
    <div class="post">
        <h3 class="title">
          {{ data.title }}
        </h3>
        <h5 class="author">
          {{ data.author }}
        </h5>
        <p class="content">
          {{ data.body }}
        </p>
    </div>
</template>

<script>
export default {
  props: {
    data: Object
  }
};
</script>

<style lang="scss" scoped>
.post {
  padding: 10px;
  background-color: rgb(204, 204, 204);

  h3,
  h5,
  p {
    margin: 0;
  }
}
</style>
