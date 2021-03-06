<template>
  <div class="home">
    <Navigation :title="'VueFlix'" />
    <Search :search="state.search" @search="handleSearch" />

    <div class="container">
      <div class="row">
        <div class="col-md-4 col-lg-3" v-for="movie in state.movies" :key="movie.imdbID"  >
          <Movie :movie="movie"/>
        </div>
      </div>
    </div>
    <div class="loader">
      <Loader class="loading" v-if="state.loading" />
    </div>
  </div>
</template>

<script>
import Navigation from '@/components/Navigation'
import Search from '@/components/Search'
import Movie from '@/components/Movie'
import Loader from '@/components/Loading'
import { reactive, watch } from 'vue'

const API_KEY = '2ac2c88b'

  export default {
    components: {
      Navigation,
      Search,
      Movie,
      Loader
    },

    // Set up composition API
    setup() {
      const state = reactive({
        search: 'joker',
        loading: true,
        movies: [],
        errorMessage: null
      })

      // Watch composition api
      watch(() => {
        const movie_url = `https://www.omdbapi.com/?s=${state.search}&apikey=${API_KEY}`
        
        fetch(movie_url)
          .then(response => response.json())
          .then(data => {
            state.movies = data.Search
            state.loading = false
          })
      })

      return {
        state,
        handleSearch(searchTerm) {
          state.loading = true
          state.search = searchTerm
          state.movies = []
        }
      }

    },
    
  }
</script>

<style scoped>
  .home {
    
  }
</style>