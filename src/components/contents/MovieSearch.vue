<template>
  <div class="movie__search">
    <h2 class="blind">검색하기</h2>
    <input
      type="search"
      v-model="searchTerm"
      @keyup.enter="search"
      placeholder="검색어를 입력해주세요!"
    />
    <button type="submit" @click="search">검색</button>
  </div>
  <!-- movie__search -->

  <section class="movie__cont">
    <h2 class="blind">영화</h2>
    <div class="movie play__icon" v-for="movie in movies" :key="movie.id">
      <a :href="'/detail/' + movie.id">
        <img :src="'https://image.tmdb.org/t/p/w500' + movie.poster_path" :alt="movie.title" />
      </a>
    </div>
  </section>
  <!-- movie__cont -->
</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios'

const movies = ref([]) //useState
const searchTerm = ref([])

const search = async () => {
  try {
    console.log(searchTerm.value)
    const response = await axios.get('https://api.themoviedb.org/3/search/movie', {
      params: {
        api_key: 'ade9889e6c6c54cbf65cc7f38a2bec71',
        language: 'ko-KR',
        query: searchTerm.value
      }
    })
    console.log(response)
    movies.value = response.data.results
    // searchResults.value = response.data;
  } catch (error) {
    console.log(error)
  }
}
// search
</script>

