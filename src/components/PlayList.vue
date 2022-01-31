<template>
  <main>
    <div v-if="!isLoaded" class="unloaded">
      <loader />
    </div>
    <div v-else class="loaded" >
    <div v-for="(disc, index) in discsList" :key="index">
      <disc-cover :disc="(disc)" />
    </div>
    </div>
  </main>
</template>

<script>
import DiscCover from "@/components/DiscCover.vue";
import Loader from "@/components/Loader.vue";

export default {
  name: "PlayList",
  components: {
    DiscCover,
    Loader
  },
  props: {
    discsList: Array,
    isLoaded:Boolean
  },
};
</script>

<style scoped lang="scss">
  main {
    width: 1200px;
    padding-top: 50px;
    margin:0 auto;

    .loaded{
      display:flex;
      flex-wrap: wrap;
      justify-content: space-between;
    }
    .unloaded{
      position:absolute;
      top:50%;
      left:50%
    }

  }
</style>

