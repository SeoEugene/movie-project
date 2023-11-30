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


            <div class="header__movie">
                <div class="movie__thumb">

                </div>
                <div class="movie__info">
                    <div class="movie__title">영화타이틀</div>
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
                    <div class="movie__launching">개봉일</div>
                </div>
            </div>
        </div>
    </header>
</template>

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