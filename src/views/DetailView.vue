<script>
import { ref, onMounted } from 'vue';
import axios from 'axios';

export default {
    setup() {
        // 영화 아이디값 가져오기
        const movieInfo = ref([]);

        const movieInfoFetch = async () => {
            try {
                const response = await axios.get('https://api.themoviedb.org/3/movie/912929', {
                    params: {
                        api_key: 'ade9889e6c6c54cbf65cc7f38a2bec71',
                        language: 'ko-KR',
                        page: '1',
                    },
                });
                // 변수에 값 저장
                movieInfo.value = response.data;
                console.log(movieInfo.value);
            } catch (err) {
                console.error(err);
            }
        };
        //  함수 실행
        onMounted(() => {
            movieInfoFetch();
        });

        return {
            movieInfo, // setup 함수에서 반환하는 것을 누락하지 않기
        };
    },
};

// 정보 내보내기
const movieInfo = ref();
try {
    const response = await axios.get('https://api.themoviedb.org/3/movie/912929', {
        params: {
            api_key: 'ade9889e6c6c54cbf65cc7f38a2bec71',
            language: 'ko-KR',
            page: '1'
        }
    });
    movieInfo.value = response.data;
    console.log(movieInfo.poster_path);
} catch (err) {
    console.log(err);
}
</script>

<template>
    <div class="info__box">
        <div class="poster">영화 포스터자리</div>
        <div class="info">영화이름자리</div>
    </div>
</template>

<style lang="scss">
.info__box {
    height: 500px;
    background-color: #fff;
    display: flex;
    margin: 0 auto;

    .poster {
        width: 50%;
        height: 500px;
        border: 1px solid red;

    }

    .info {
        width: 50%;
        height: 500px;
    }
}
</style>