<script setup>
import { onMounted, ref } from 'vue'
import axios from 'axios'
import HeaderSection from '@/components/section/HeaderSection.vue'
import MovieSearch from '@/components/contents/MovieSearch.vue'
import MovieTag from '@/components/contents/MovieTag.vue'
// import MovieCont from '@/components/contents/MovieCont.vue'
import FooterSection from '@/components/section/FooterSection.vue'

const movies = ref([])

const fetchMovies = async (moviesData) => {
  movies.value = moviesData
}

onMounted(async () => {
  // 초기 페이지 로딩 시 최신 영화를 가져옴
  await fetchMovies('latest')
})
</script>

<template>
  <HeaderSection />
  <main id="main" role="main">
    <div class="container">
      <div class="movie__inner">
        <MovieSearch />
        <MovieTag :fetchMovies="fetchMovies" />
        <!-- <MovieCont /> -->
      </div>
    </div>
  </main>
  <FooterSection />
</template>

<script>
export default {
  name: 'MovieHomePage',
  components: {
    HeaderSection,
    MovieSearch,
    MovieTag,
    // MovieCont,
    FooterSection
  },
  data() {
    return {
      movies: []
    }
  },
  methods: {}
}
</script>

<style lang="scss">
.movie__inner {
  display: block;
  justify-content: space-between;

  .movie__search {
    margin-top: 50px;
    display: flex;
    justify-content: center;

    input {
      width: 60%;
      height: 40px;
      border: none;
      border-bottom: 2px solid #ff9a9e;
      background-color: #2b2b2b;
      outline: none;
      font-size: 18px;
      color: #fdfdfd;
    }

    button {
      width: 8%;
      height: 40px;
      border: none;
      border-radius: 30px;
      background: linear-gradient(to right, #ff9a9e, #fecfef);
      color: #2b2b2b;
      font-weight: 800;
      margin-left: 10px;
      cursor: pointer;
    }
  }

  .movie__tag {
    margin-top: 50px;

    ul {
      display: flex;
      justify-content: center;
    }

    a {
      margin: 5px;
      padding: 10px 20px;
      border: 2px solid #ff9a9e;
      border-radius: 30px;

      &:hover {
        background-color: #fecfef;
        font-weight: 600;
      }
    }
  }

  .movie__cont {
    margin-top: 30px;
    display: flex;
    flex-wrap: wrap;

    .movie {
      width: 25%;
      height: 525px;
      background-color: #ccc;
    }
  }
}

@media (max-width: 1000px) {
  .movie__inner {
    border: 1px solid #ffb2b2;
  }
}
</style>