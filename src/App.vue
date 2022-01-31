<template>
  <div id="app">
    <app-header />
    <play-list :discsList="discsList" />
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
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((result) => {
        this.discsList = result.data.response;
      });
  },
};
</script>

<style lang="scss">
@import "./style/main.scss";
</style>
