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

</style>
