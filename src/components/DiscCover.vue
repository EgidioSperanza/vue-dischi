<template>
  <div class="disc-cover">
    <div>
      <img :src="disc.poster" :alt="disc.title" />
      <h2>{{ disc.title }}</h2>
    </div>

    <div>
      <p>{{ disc.author }}</p>
      <p>{{ disc.year }}</p>
    </div>
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
.disc-cover {
  width: calc((1200px / 5) - 30px);
  height: 400px;
  background-color: $primary-light-color;
  padding: 20px;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: space-between;

  img {
    width: 100%;
    margin-bottom: 20px;
  }

  h2 {
    text-transform: uppercase;
    margin-bottom: 20px;
  }

  p {
    color: $text-info-color;
  }
}
</style>

