<template>
  <div id="app">
    <app-header />
    <play-list :discsList="discsList" :isLoaded="isLoaded"/>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import PlayList from "./components/PlayList.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    AppHeader,
    PlayList,
  },
  data() {
    return {
      discsList: [],
      isLoaded:false
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((result) => {
        this.discsList = result.data.response;
        this.isLoaded=true;
      });
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
