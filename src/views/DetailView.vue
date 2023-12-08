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
            <!-- 영화 썸네일 -->
            <DetailIntro v-if="movieBasic" :movieBasic="movieBasic" />
            <!-- 영화 정보 -->
            <DetailInfo v-if="movieInfo" :movieInfo="movieInfo" />
            <!--<DetailReview v-if="movieReview" :movieReview="movieReview" />
    <DetailCredits v-if="movieCredits" :movieCredits="movieCredits" /> -->
        </div>
    </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';
import axios from 'axios';

import DetailIntro from "../components/detail/DetailIntro.vue";
import DetailInfo from "../components/detail/DetailInfo.vue";
// import DetailReview from "../components/detail/DetailReview.vue";
// import DetailCredits from "../components/detail/DetailCredits.vue";

export default {
    name: "MovieDetailPage",
    components: {
        DetailIntro,
        DetailInfo,
        // DetailReview,
        // DetailCredits,
    },

    setup() {
        const movieBasic = ref(null);
        const movieInfo = ref(null);
        const movieReview = ref(null);
        const movieCredits = ref(null);

        const route = useRoute();

        onMounted(async () => {
            // get방식
            const movieId = route.params.movieId;
            // api키 값 가져오기 (.env)
            const apiKey = import.meta.env.VITE_API_KEY;
            // 언어 설정
            const language = "ko-KR";

            try {
                const resMovieBasic = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                console.log(resMovieBasic.data);
                movieBasic.value = resMovieBasic.data;

                const resMovieInfo = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                movieInfo.value = resMovieInfo.data;

                // const resMovieReview = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                // movieReview.value = resMovieReview.data;

                // const resmovieCredits = await axios.get(`https://api.themoviedb.org/3/movie/${movieId}?language=${language}&api_key=${apiKey}`);
                // movieCredits.value = resmovieCredits.data;

            } catch (err) {
                console.log(err);
            }
        });

        return { movieBasic };
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
    display: flex;


}
</style>