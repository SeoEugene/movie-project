<script setup>
import { ref } from 'vue';
import axios from 'axios';

// headermovie에 개봉영화 리스트를 가져옴
const headermovie = ref([]);

// 개봉 예정 영화 가져오기
// try {
//     const response = await axios.get('https://api.themoviedb.org/3/movie/upcoming', {
//         params: {
//             api_key: 'ade9889e6c6c54cbf65cc7f38a2bec71',
//             language: 'ko-KR',
//             page: '1'
//         }
//     });
//     // 데이터 구조 : data.results (모든 데이터정보)
//     headermovie.value = response.data.results;

//     // 데이터 5개만 가져오기
//     headermovie.value = response.data.results.slice(0, 5);
//     console.log(headermovie.value);

// } catch (err) {
//     console.log(err);
// }

</script>

<template>
    <header id="header" role="banner">
        <h2 class="logo">CINE</h2>
        <div class="header__inner">
            <div class="header__banner"></div>

            <div class="header__movie" v-for="movie in top5Movies" :key="movie.id">
                <div class="movie__thumb">
                    <img :src="'https://image.tmdb.org/t/p/w500' + movie.poster_path" :alt="movie.title">
                </div>

                <div class="movie__info">
                    <h3>{{ movie.title }}</h3>
                </div>
            </div>
        </div>
    </header>
</template>

<style lang="scss">
.logo {
    width: 100%;
    height: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 10px;
}

.header__banner {
    width: 100%;
    height: 250px;
    background-image: url('@/assets/img/Header.png');
    background-position: center;
    background-repeat: no-repeat;
    background-size: contain;
}

.header__movie {
    border: 1px solid pink;
    width: 100%;
    height: 630px;
    display: flex;


    .movie__thumb {
        border: 1px solid red;
        width: 40%;
    }

    .movie__info {
        border: 1px solid orange;
        width: 60%;
    }
}
</style>