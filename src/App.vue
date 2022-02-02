<template>
  <div id="app">
    <app-header
      :discsByGenre="discsByGenre"
      :discsByAuthor="discsByAuthor"
      @filterBy="filterBy"
    />
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
        this.discsByGenre = this.discsList.map((disc) => disc.genre)
        this.discsByGenre = this.discsByGenre.filter(
          (genre, i) => this.discsByGenre.indexOf(genre) == i,
        )
        this.discsByAuthor = this.discsList.map((disc) => disc.author)
        this.discsByAuthor = this.discsByAuthor.filter(
          (author, i) => this.discsByAuthor.indexOf(author) == i,
        )
        this.isLoaded = true
      })
  },
  methods: {
    filterBy(type, el) {
      if (el === 'all' || el === '') {
        this.discsListFiltered = this.discsList
      } else {
        this.discsListFiltered = this.discsList.filter((disc) => {
          if (type === 'title') {
            return disc.title.toLowerCase().includes(el.toLowerCase())
          }else{
            return disc[type].includes(el)
          }
        })
      }
    },
  },
}
</script>

<style lang="scss">
@import './style/main.scss';
</style>
