<template>
  <h3>감독</h3>
  <ul>
    <li>
      <img
        v-if="movieCredits.crew[0].profile_path"
        :src="getPostPath(movieCredits.crew[0].profile_path)"
        :alt="movieCredits.crew[0].name"
      />
      <img v-else src="../../assets/img/noneimg.png" :alt="movieCredits.crew[0].name" />
      <div class="name">{{ movieCredits.crew[0].name }}</div>
    </li>
  </ul>
  <h3>영화배우</h3>
  <ul>
    <li v-for="actors in movieCredits.cast.slice(0, 10)" :key="actors.id">
      <img v-if="actors.profile_path" :src="getPostPath(actors.profile_path)" :alt="actors.name" />
      <img v-else src="../../assets/img/noneimg.png" :alt="actors.name" />
      <div class="name">{{ actors.name }}</div>
    </li>
  </ul>
</template>
<script>
export default {
  props: {
    movieCredits: Object
  },
  methods: {
    getPostPath(posterPath) {
      return `https://image.tmdb.org/t/p/w500${posterPath}`
    }
  }
}
</script>

