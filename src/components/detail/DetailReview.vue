<template>
  <h3>리뷰</h3>
  <div v-if="movieReview.results.length === 0" class="review__none">
    리뷰가 없습니다. 리뷰를 작성해주세요.
  </div>
  <div class="review" v-for="author in movieReview.results" :key="author.author_details.id">
    <div>
      <!-- <img :src="author.author_details.url" :alt="author.author" /> -->
      <div class="name">{{ author.author }}</div>
    </div>
    <div class="comment">{{ author.content }}</div>
  </div>
</template>
<script>
export default {
  props: {
    movieReview: Object
  },
  methods: {
    getPostPath(posterPath) {
      return `https://image.tmdb.org/t/p/w500${posterPath}`
    }
  }
}
</script>
