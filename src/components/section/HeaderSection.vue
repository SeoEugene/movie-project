<template>
  <header id="header" role="banner">
    <h2 class="logo">CINE</h2>
    <div class="header__inner">
      <div class="header__banner"></div>

      <div class="header__movie" v-if="slidemovie.length &gt; 0">
        <transition name="fade" mode="out-in">
          <div class="movie__background">
            <div class="movie__box">
              <div class="movie__thumb">
                <img :src="getPostPath(slidemovie[0].backdrop_path)" :alt="slidemovie[0].title" />
              </div>
              <div class="movie__info">
                <div class="movie__title">{{ slidemovie[0].title }}</div>
                <div class="movie__desc">{{ slidemovie[0].overview }}</div>
                <!-- <div class="movie__actor">
                  <h3>영화배우</h3>
                  <ul>
                    <li>
                      <img src="" alt="감독" />
                      <div class="name">감독</div>
                    </li>
                    <li>
                      <img src="" alt="주연배우" />
                      <div class="name">배우</div>
                    </li>
                    <li>
                      <img src="" alt="주연배우" />
                      <div class="name">배우</div>
                    </li>
                    <li>
                      <img src="" alt="주연배우" />
                      <div class="name">배우</div>
                    </li>
                    <li>
                      <img src="" alt="주연배우" />
                      <div class="name">배우</div>
                    </li>
                  </ul>
                </div> -->
                <div class="movie__launching">{{ slidemovie[0].release_date }}</div>
              </div>
            </div>
            <!-- movie__box -->
          </div>
          <!-- movie__background -->
        </transition>
      </div>
    </div>
    <!-- header__inner -->
  </header>
</template>

<script>
import { ref, onMounted } from 'vue'
import axios from 'axios'

export default {
  setup() {
    const slidemovie = ref([])
    const index = 0

    // 이미지 url
    const getPostPath = (posterPath) => {
      return `https://image.tmdb.org/t/p/w500${posterPath}`
    }

    // api key
    onMounted(async () => {
      const apiKey = import.meta.env.VITE_API_KEY
      const language = 'ko-KR'

      try {
        const resslidemovie = await axios.get(
          `https://api.themoviedb.org/3/movie/now_playing?language=${language}&page=1`,
          {
            params: {
              api_key: apiKey,
              language: language,
              page: '1'
            }
          }
        )
        console.log(resslidemovie.data.results)
        // api 데이터 추출
        slidemovie.value = resslidemovie.data.results

        // const postData = {
        //   data: slidemovie.id
        // }
        // const response = await axios.post('')
      } catch (err) {
        console.log(err)
      }
    })

    // 여기서 데이터를 반환합니다.
    return { slidemovie, getPostPath }
  }
}
</script>

<style lang="scss">
.logo {
  width: 100%;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding-top: 20px;
}

.header__banner {
  width: 100%;
  height: 250px;
  background-image: url('@/assets/img/Header.png');
  background-position: center;
  background-repeat: no-repeat;
  background-size: contain;
  margin-top: 20px;
}

.header__movie {
  width: 100%;
  height: 100vh;
  position: relative;

  .fade-enter-active,
  .fade-leave-active {
    transition: opacity 1s; /* 트랜지션 지속시간을 조절할 수 있습니다. */
  }
  .fade-enter,
  .fade-leave-to {
    opacity: 0;
  }

  .movie__background {
    position: absolute;
    top: 0;
    left: 0;
    .movie__box {
      display: flex;
      .movie__thumb {
        width: 50%;
        img {
          width: 50vw;
        }
      }
      .movie__info {
        width: 50%;
        display: block;
        .movie__title {
        }
        .movie__desc {
        }
        .movie__actor {
        }
        .movie__launching {
        }
      }
    }
  }
}
</style>