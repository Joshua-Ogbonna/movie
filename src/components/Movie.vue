<template>
    
   <div class="movie">
       <h2> {{movie.Title}} </h2>
       <div>
           <img :src="movie.Poster" alt="altText" width="200">
       </div>
       <p> Year Produced: {{movie.Year}} </p>
   </div>
</template>

<script>
import { computed } from '@vue/runtime-core'
    

    export default {
        name: 'Movie',
        props: ['movie'],

        setup(props) {
            const altText = computed(() => {
                `The movie titled ${props.movie.Title}`
            })
            return {
                altText
            }
        }
    }
</script>

<style scoped>
    .movie {
        font-family: 'Open Sans', sans-serif;
    }
    .movie h2 {
        font-weight: 800;
        font-size: 1.2rem;
    }
    .movie p {
        font-weight:600;
    }
    
    @media only screen and (max-width: 736px) {
        img {
            width: 100%;
        }
        .movie h2 {
            font-size: 1.3rem;
        }
    }
    @media only screen and (min-width: 768px) and (max-width: 1024px) {
        .movie h2 {
            font-size: 1.3rem;
        }
    }
</style>