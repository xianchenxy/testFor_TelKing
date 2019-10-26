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
        font-size: 62.5%;
    }

    body {
        font-size: 100%;
        background-color: #f5f8f9;
        color: #262b2e;
    }

    div#app {
        /*max-width: 950px;*/
        /*padding: 0 125px;*/
        /*margin: 0 auto;*/
    }
</style>
