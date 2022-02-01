<template>
  <header>
    <i class="fab fa-spotify"></i>
    <select v-model="selectedGenre">
      <option disabled value="">Please select one</option>
      <option v-for="(genre, index) in discsByGenre" :key="index">
        {{ genre }}
      </option>
    </select>
    <span>Selected: {{ selectedGenre }}</span>
    <select v-model="selectedAuthor">
      <option disabled value="">Please select one</option>
      <option v-for="(author, index) in discsByAuthor" :key="index">
        {{ author }}
      </option>
    </select>
    <span>Selected: {{ selectedAuthor }}</span>
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
    discsByAuthor:Array,
  },
}
</script>

<style scoped lang="scss">
@import '@/style/variables.scss';
header {
  height: 50px;
  background-color: $primary-light-color;
  padding-left: 20px;
  display: flex;
  align-items: center;
}
i {
  color: $logo-color;
  font-size: 30px;
}
</style>
