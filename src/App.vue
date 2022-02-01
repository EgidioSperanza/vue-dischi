<template>
  <div id="app">
    <app-header :discsByGenre="discsByGenre" :discsByAuthor="discsByAuthor" />
    <play-list :discsList="discsListFiltered" :isLoaded="isLoaded" />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import PlayList from './components/PlayList.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    AppHeader,
    PlayList,
  },
  data() {
    return {
      discsList: [],
      discsListFiltered: [],
      discsByGenre: [],
      discsByAuthor: [],
      isLoaded: false,
    }
  },
  mounted() {
    axios
      .get('https://flynn.boolean.careers/exercises/api/array/music')
      .then((result) => {
        this.discsList = result.data.response
        this.discsListFiltered = this.discsList
        this.discsList.filter((disc) => {
          if (!this.discsByGenre.includes(disc.genre)) {
            this.discsByGenre.push(disc.genre)
          }
        })
        this.discsList.filter((disc) => {
          if (!this.discsByAuthor.includes(disc.author)) {
            this.discsByAuthor.push(disc.author)
          }
        })
        this.isLoaded = true
      })
  },
}
</script>

<style lang="scss">
@import './style/main.scss';
</style>
