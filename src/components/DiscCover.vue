<template>
  <div class="disc-cover">
  </div>
</template>

<script>
export default {
  name: "DiscCover",
    props: {
    disc: Object,
  },

};
</script>

<style scoped lang="scss">
@import "@/style/variables.scss";
  .disc-cover{
    width: calc((1200px / 5) - 30px);
    height: 300px;
    background-color: $primary-light-color;
    margin-bottom: 20px;
    padding: 20px;
  }
</style>

