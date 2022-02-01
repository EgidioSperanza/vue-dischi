<template>
  <header>
    <i class="fab fa-spotify"></i>
    <div class="filters">
      <span>Filtra per Genere</span>
      <select v-model="selectedGenre" @change="filterByGender()">
        <option disabled value="">Please select one</option>
        <option value="">All</option>
        <option v-for="(genre, index) in discsByGenre" :key="index">
          {{ genre }}
        </option>
      </select>
      <span>Filtra per Autore</span>
      <select v-model="selectedAuthor" @change="filterByAuthor()">
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
    }
  },
  props: {
    discsByGenre: Array,
    discsByAuthor: Array,
  },
  methods: {
    filterByGender() {
      this.selectedAuthor = ''
      this.$emit('filterByGenre', this.selectedGenre)
    },
    filterByAuthor() {
      this.selectedGenre = ''
      this.$emit('filterByAuthor', this.selectedAuthor)
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
.filters{
  display: flex;
  flex-direction: column;
  margin-right: 20px;
}
</style>
