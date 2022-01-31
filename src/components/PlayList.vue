<template>
  <main>
    <div v-for="(disc, index) in discsList" :key="index">
      <disc-cover :disc="disc" />
    </div>
  </main>
</template>

<script>
import DiscCover from "@/components/DiscCover.vue";

export default {
  name: "PlayList",
  components: {
    DiscCover
  },
  props: {
    discsList: Array,
    waitUntil:Number
  },
};
</script>

<style scoped lang="scss">
  main {
    width: 1200px;
    padding-top: 50px;
    margin:0 auto;
    display:flex;
    flex-wrap: wrap;
    justify-content: space-between;

  }
</style>

