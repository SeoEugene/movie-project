<template>
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
</template>

<script>
export default {
    props: {
        movieInfo: Object,
    },
}
</script>

<style lang="scss">
.movie__info {
    border: 1px solid orange;
    width: 50%;
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
        height: 500px;
    }
}
</style>