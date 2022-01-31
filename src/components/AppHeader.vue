<template>
  <header>
    <i class="fab fa-spotify"></i>
  </header>
</template>

<script>
export default {
  name: "AppHeader",
  props: {},
};
</script>

<style scoped lang="scss">
@import "@/style/variables.scss";
header {
  height: 50px;
  background-color: $primary-light-color;
  padding-left:20px;
  display: flex;
  align-items: center;
}
i {
  color: $logo-color;
  font-size: 30px;
}
</style>

