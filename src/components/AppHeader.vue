<template>
  <header>
    <i class="fab fa-spotify"></i>
    <div class="search">
      <input
        type="text"
        placeholder="Please write about the title of the album and press enter"
        v-model="typedTitle"
        @input="searchByType"
      />
      <button @click="searchTypeReset">Reset</button>
    </div>
    <div class="filters">
      <span>Filtra per Genere</span>
      <select v-model="selectedGenre" @change="filterByGender">
        <option disabled value="">Please select one</option>
        <option value="all">All</option>
        <option v-for="(genre, index) in discsByGenre" :key="index">
          {{ genre }}
        </option>
      </select>
      <span>Filtra per Autore</span>
      <select v-model="selectedAuthor" @change="filterByAuthor">
        <option disabled value="">Please select one</option>
        <option value="">All</option>
        <option v-for="(author, index) in discsByAuthor" :key="index">
          {{ author }}
        </option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
  name: 'AppHeader',
  data() {
    return {
      selectedGenre: '',
      selectedAuthor: '',
      typedTitle: '',
    }
  },
  props: {
    discsByGenre: Array,
    discsByAuthor: Array,
  },
  methods: {
    filterByGender() {
      this.selectedAuthor = ''
      this.$emit('filterBy', 'genre', this.selectedGenre)
    },
    filterByAuthor() {
      this.selectedGenre = ''
      this.$emit('filterBy', 'author', this.selectedAuthor)
    },
    searchByType() {
      this.$emit('filterBy', 'title', this.typedTitle)
    },
    searchTypeReset() {
      this.selectedAuthor = ''
      this.selectedGenre = ''
      this.typedTitle = ''
      this.$emit('filterBy', 'title', this.typedTitle)
    },
  },
}
</script>

<style scoped lang="scss">
@import '@/style/variables.scss';
header {
  height: 100px;
  background-color: $primary-light-color;
  padding-left: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
i {
  color: $logo-color;
  font-size: 60px;
}
input {
  width: 500px;
  height: 50px;
  line-height: 50px;
}
button {
  height: 50px;
  margin-left: 20px;
  padding: 0 20px;
  background-color: $background-color;
  color: $text-color;
  border-radius: 10px;
}
.filters {
  display: flex;
  flex-direction: column;
  margin-right: 20px;
}
</style>
