<template>
  <div class="home">
    <Hero />
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      movies: [],
    }
  },

  async fetch() {
    await this.getMovies()
  },

  methods: {
    async getMovies() {
      const data = axios.get(
        `https://api.themoviedb.org/3/movie/now_playing?api_key=114888fa1dd2d3f986b639d6bb97e22c&language=en-US&page=1`
      )
      const result = await data
      result.data.results.forEach((movie) => {
        this.movies.push(movie)
      })
    },
  },
}
</script>
