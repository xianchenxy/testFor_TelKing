<template>
    <div id="app">
        <appHeader></appHeader>
        <appHome></appHome>
        <appFooter></appFooter>
    </div>
</template>

<script>
    import Home from './components/Home/Home.vue';
    import Header from './components/Header/Header.vue';
    import Footer from './components/Footer/Footer.vue';

    export default {
        components: {
            appHome: Home,
            appHeader: Header,
            appFooter: Footer
        }
    }
</script>

<style>
    html {
        font-size: 62.5%; /* 1440px -> 1rem = 10px */
    }

    body {
        background-color: #f5f8f9;
        color: #262b2e;
    }

    @media screen and (max-width: 1080px) {
        html {
            font-size: 50%;
        }

        /*body {*/
        /*background-color: lightseagreen !important;*/
        /*}*/
    }

    .logo {
        float: left;
        width: 10.7rem;
        height: 3.2rem;
        line-height: 3.2rem;
        text-align: center;
        font-size: 1.2rem;
        -webkit-border-radius: .5rem;
        -moz-border-radius: .5rem;
        border-radius: .5rem;
        background-color: #f92525;
        cursor: pointer;
    }

    .logo:hover {
        opacity: .8;
    }
</style>
