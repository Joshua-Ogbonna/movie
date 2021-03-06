<template>
    <div>
        <!-- Image and text -->
        <nav class="navbar" id="nav">
            <a class="navbar-brand" href="#">
                <!-- <img src="/docs/4.3/assets/brand/bootstrap-solid.svg" width="30" height="30" class="d-inline-block align-top" alt=""> -->
                {{title}}   
            </a>
        </nav>
    </div>
</template>

<script>
    export default {
        name: 'Navigation',
        props: ['title'],
        setup() {}
    }
</script>

<style scoped>
    #nav {
        background: #1a1c20;
        padding: 2rem 2rem;
    }
    .navbar-brand {
        font-family: 'Open Sans', sans-serif;
        font-weight: 800;
        font-size: 2rem;
        color: rgba(247, 48, 48, 0.753);
    }
    .navbar-brand:hover {
        color: #fff;
    }
    @media only screen and (max-width: 736px) {
        #nav {
            /* background: #1a1c20; */
            padding: 2rem 1rem;
        }
    }
</style>