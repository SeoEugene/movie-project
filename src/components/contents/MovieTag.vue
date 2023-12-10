<template>
  <div class="movie__tag">
    <ul>
      <li><a href="#" @click="fetchMovies('latest')">최신영화</a></li>
      <li><a href="#" @click="fetchMovies('popular')">인기영화</a></li>
      <li><a href="#" @click="fetchMovies('top_rated')">영화 순위</a></li>
      <li><a href="#" @click="fetchMovies('upcoming')">개봉예정</a></li>

      <!-- <li><a href="#">공포영화</a></li>
            <li><a href="#">액션영화</a></li>
            <li><a href="#">슬픈영화</a></li> -->
    </ul>
  </div>
  <!-- movie__tab -->

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

const movies = ref([])

const fetchMovies = async (category) => {
  let url = 'https://api.themoviedb.org/3/movie/popular'

  switch (category) {
    case 'latest':
      url = 'https://api.themoviedb.org/3/movie/now_playing'
      break

    case 'popular':
      url = 'https://api.themoviedb.org/3/movie/popular'
      break

    case 'top_rated':
      url = 'https://api.themoviedb.org/3/movie/top_rated'
      break

    case 'upcoming':
      url = 'https://api.themoviedb.org/3/movie/upcoming'
      break
  }

  try {
    const response = await axios.get(url, {
      params: {
        api_key: 'ade9889e6c6c54cbf65cc7f38a2bec71',
        language: 'ko-KR',
        page: '1'
      }
    })
    console.log(response)
    movies.value = response.data.results
  } catch (err) {
    console.log(err)
  }
}
// fetchMovies

// export default {}
</script>
