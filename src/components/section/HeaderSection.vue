<template>
    <header id="header" role="banner">
        <h2 class="logo">CINE</h2>
        <div class="header__inner">
            <div class="header__banner"></div>


            <div class="header__movie" v-for="(movie, index) in slidemovie" :key="index">
                <div class="movie__thumb">
                    <img :src="getPostPath(movie.poster_path)" :alt="movie.title" />
                </div>
                <div class="movie__info">
                    <div class="movie__title">{{ movie.title }}</div>
                    <div class="movie__desc">영화 내용</div>
                    <div class="movie__actor">
                        <h3>영화배우</h3>
                        <ul>
                            <li><img src="" alt="감독">
                                <div class="name">감독</div>
                            </li>
                            <li><img src="" alt="주연배우">
                                <div class="name">배우</div>
                            </li>
                            <li><img src="" alt="주연배우">
                                <div class="name">배우</div>
                            </li>
                            <li><img src="" alt="주연배우">
                                <div class="name">배우</div>
                            </li>
                            <li><img src="" alt="주연배우">
                                <div class="name">배우</div>
                            </li>
                        </ul>
                    </div>
                    <div class="movie__launching">{{ movie.release_date }}</div>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
import { ref, onMounted } from 'vue';
import axios from 'axios';

export default {
    setup() {
        const slidemovie = ref(null);

        const getPostPath = (posterPath) => {
            return `https://image.tmdb.org/t/p/w500${posterPath}`;
        };

        onMounted(async () => {
            const apiKey = import.meta.env.VITE_API_KEY;
            const language = 'ko-KR';

            try {
                const resslidemovie = await axios.get(
                    `https://api.themoviedb.org/3/movie/now_playing?language=${language}&page=1`, {
                    params: {
                        api_key: apiKey,
                        language: language,
                        page: '1'
                    }
                })
                console.log(resslidemovie.data.results);
                slidemovie.value = resslidemovie.data.results;

                const postData = {
                    data: slidemovie.id,
                };

                const response = await axios.post('')


            } catch (err) {
                console.log(err);
            }
        });

        // 여기서 데이터를 반환합니다.
        return { slidemovie, getPostPath };
    },
};
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
    display: flex;
    padding: 30px;
    background-color: #000;
    margin-top: 20px;


    .movie__thumb {
        border: 1px solid red;
        width: 40%;
    }

    .movie__info {
        border: 1px solid orange;
        width: 60%;
        padding: 20px;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;

        div {
            margin-top: 10px;
        }

        .movie__title {
            width: 100%;
            text-align: center;
            font-weight: 800;
            font-size: 40px;
        }

        .movie__desc {
            width: 100%;
        }

        .movie__actor {
            width: 100%;

            ul {
                display: flex;
                flex-wrap: wrap;
                ;
                justify-content: center;
                text-align: center;

                li {
                    border: 1px solid #fff;

                    img {
                        display: flex;
                        width: 150px;
                        height: 150px;
                    }
                }
            }
        }

        .movie__launching {
            width: 100%;
        }
    }
}
</style>