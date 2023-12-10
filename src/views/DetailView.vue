<template>
  <div>
    <header id="header" role="banner">
      <div class="header__inner">
        <div class="header__nav">
          <h1><a href="/">CINE</a></h1>
        </div>
      </div>
    </header>

    <div class="movie__box">
      <div class="movie__info">
        <!-- 영화 썸네일 -->
        <DetailIntro v-if="movieBasic" :movieBasic="movieBasic" />
        <!-- 영화 정보 -->
        <DetailInfo v-if="movieInfo" :movieInfo="movieInfo" />
      </div>
      <div class="movie__actor">
        <!-- 영화 배우 -->
        <DetailCredits v-if="movieCredits" :movieCredits="movieCredits" />
      </div>
    </div>
    <div class="movie__review">
      <!-- 영화 리뷰 -->
      <DetailReview v-if="movieReview" :movieReview="movieReview" />
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'
import axios from 'axios'
import DetailIntro from '@/components/detail/DetailIntro.vue'
import DetailInfo from '@/components/detail/DetailInfo.vue'
import DetailCredits from '@/components/detail/DetailCredits.vue'
import DetailReview from '@/components/detail/DetailReview.vue'

export default {
  name: 'MovieDetailPage',
  components: {
    DetailIntro,
    DetailInfo,
    DetailCredits,
    DetailReview
  },

  setup() {
    const movieBasic = ref(null)
    const movieInfo = ref(null)
    const movieCredits = ref(null)
    const movieReview = ref(null)

    const route = useRoute()

    onMounted(async () => {
      // get방식
      const movieId = route.params.movieId
      // api키 값 가져오기 (.env)
      const apiKey = import.meta.env.VITE_API_KEY
      // 언어 설정
      const language = 'ko-KR'

      try {
        const resMovieBasic = await axios.get(
          `https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`
        )
        console.log(resMovieBasic.data)
        movieBasic.value = resMovieBasic.data

        const resMovieInfo = await axios.get(
          `https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`
        )
        movieInfo.value = resMovieInfo.data

        const resmovieCredits = await axios.get(
          `https://api.themoviedb.org/3/movie/${movieId}/credits?language=${language}&api_key=${apiKey}`
        )
        console.log(resmovieCredits.data)
        movieCredits.value = resmovieCredits.data

        const resMovieReview = await axios.get(
          `https://api.themoviedb.org/3/movie/${movieId}/reviews?language=${language}&api_key=${apiKey}`
        )
        console.log(resMovieReview.data)
        movieReview.value = resMovieReview.data
      } catch (err) {
        console.log(err)
      }
    })

    return { movieBasic, movieInfo, movieCredits, movieReview }
  }
}
</script>

<style lang="scss">
.header__inner {
  width: 100%;
  text-align: center;
}

.movie__box {
  width: 100%;
  .movie__info {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px 5%;
    .movie__thumb {
      width: 50%;
      padding: 0 10%;
      background-position: center;
      background-size: cover;
    }
    .movie__info {
      width: 50%;
      display: block;

      .movie__title {
        font-size: 30px;
        margin-bottom: 20px;
      }
      .movie__desc {
        margin-bottom: 20px;
        font-size: 18px;
      }
      > span {
        display: inline-block;
        margin-bottom: 20px;
        font-size: 18px;
      }
      .movie__runtime,
      .movie__launching {
        font-size: 18px;
        margin-bottom: 20px;
      }
    }
  }

  .movie__actor {
    width: 100%;
    padding: 3% 10%;

    h3 {
      font-size: 30px;
      margin-top: 20px;
    }

    ul {
      display: flex;
      flex-wrap: wrap;
      justify-content: left;
      text-align: center;

      li {
        padding: 5px;
        img {
          display: flex;
          width: 150px;
          height: 150px;
        }
      }
    }
  }
}
.movie__review {
  width: 100%;
  padding: 3% 10%;

  h3 {
    font-size: 30px;
  }
  .review__none {
    font-size: 18px;
    min-height: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .review {
    margin-top: 20px;
    border-bottom: 1px solid #fff;
    padding-bottom: 50px;
    .name {
      font-size: 24px;
      margin-bottom: 10px;
    }
    .comment {
      font-size: 18px;
    }
  }
}
</style>