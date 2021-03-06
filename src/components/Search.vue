<template>
    <div>
        <form class="search">
            <input type="text" class="form-control" :value="movieTitle" @keyup="handleChange">
            <button class="btn btn-dark mt-2" @click="handleSubmit">Submit</button>
        </form>
    </div>
</template>

<script>
import { ref } from '@vue/reactivity'
    export default {
        name: 'Search',
        props: ['search'],

        // Set up composition api
        setup(props, {emit}){ 
            const movieTitle = ref(props.search)

            return {
                movieTitle,

                // Handle submit function
                handleSubmit(event) {
                    event.preventDefault()
                    emit('search', movieTitle.value)
                    // props.loading = true
                },
                // Handle change event function
                handleChange(event) {
                    movieTitle.value = event.target.value
                }
            }
        }
    }
</script>

<style scoped>
    form {
        width: 1000px;
        margin: 2rem auto;
    }
    @media only screen and (max-width: 736px) {
        form {
            width: 300px;
            margin: 2rem auto;
        }   
    }
    @media only screen and (min-width: 768px) and (max-width: 1024px) {
        form {
            width: 700px;
            margin: 2rem auto;
        }
    }
</style>