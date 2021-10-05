<template>
  <div class="home">
    <Hero />
    <div class="movies">
      <div class="movie-grid">
        <div v-for="(movie, index) in movies" :key="index" class="movie-card">
          <img
            :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`"
            alt=""
          />
          <div class="movie-info">
            <p class="title">{{ movie.title }}</p>
            <p class="release">
              Released:
              {{
                new Date(movie.release_date).toLocaleString('en-us', {
                  month: 'long',
                  day: 'numeric',
                  year: 'numeric',
                })
              }}
            </p>
            <p class="rating">Rating: {{ movie.vote_average }}</p>
          </div>
          <NuxtLink
            :to="{ name: 'movies-movieid', params: { movieid: movie.id } }"
            class="button"
          >
            More info
          </NuxtLink>
        </div>
      </div>
    </div>
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


<style lang="scss">
.movies {
  max-width: 1400px;
  margin: 0 auto;
  padding: calc(var(--spacing-base) * 2);
  color: var(--text-white);

  .movie-grid {
    display: grid;
    column-gap: calc(var(--spacing-base) * 2);
    row-gap: calc(var(--spacing-base) * 4);
    grid-template-columns: repeat(2, 1fr);
    
    @media only screen and (min-width: 768px) {
      grid-template-columns: repeat(4, 1fr);
    }

    .movie-card {
      display: flex;
      flex-direction: column;
      background: var(--bg-secondary);

      img {
        width: 100%;
        height: 100%;
      }

      .movie-info {
        margin: var(--spacing-base);
      }
    }
  }
}
</style>