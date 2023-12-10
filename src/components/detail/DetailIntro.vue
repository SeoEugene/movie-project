<template>
  <div class="movie__thumb">
    <img :src="getPostPath(movieBasic.poster_path)" :alt="movieBasic.spoken_languages.title" />
    <!-- {{ movieBasic.poster_path }} -->
  </div>
</template>

<script>
export default {
  // get
  props: {
    movieBasic: Object
  },
  methods: {
    getPostPath(posterPath) {
      return `https://image.tmdb.org/t/p/w500${posterPath}`
    }
  }
}
</script>

