<template>
  <div class="movie__info">
    <div class="movie__title">{{ movieInfo.title }}</div>
    <div class="movie__desc">{{ movieInfo.overview }}</div>
    <span>
      장르 :
      <span class="movie__genres" v-for="genres in movieInfo.genres" :key="genres.id">
        {{ genres.name }},
      </span>
    </span>
    <div class="movie__runtime">상영시간 :{{ formattedRuntime }}</div>
    <div class="movie__launching">개봉일 : {{ movieInfo.release_date }}</div>
  </div>
</template>

<script>
export default {
  props: {
    movieInfo: Object
  },
  computed: {
    formattedRuntime() {
      if (this.movieInfo && this.movieInfo.runtime) {
        const totalMinutes = this.movieInfo.runtime
        const hours = Math.floor(totalMinutes / 60)
        const minutes = totalMinutes % 60
        return `${hours}시간 ${minutes}분`
      } else {
        return ''
      }
    }
  }
}
</script>

