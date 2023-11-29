<template>
    <div class="movie__tag">
        <ul>
            <li><a href="#" @click="fetchMovies('latest')">최신영화</a></li>
            <li><a href="#" @click="fetchMovies('popular')">인기영화</a></li>
            <li><a href="#" @click="fetchMovies('top_rated')">영화 순위</a></li>
            <li><a href="#" @click="fetchMovies('upcoming')">개봉예정</a></li>

            <li><a href="#">공포영화</a></li>
            <li><a href="#">액션영화</a></li>
            <li><a href="#">슬픈영화</a></li>
        </ul>
    </div>
</template>

<script>
export default {

}
</script>
