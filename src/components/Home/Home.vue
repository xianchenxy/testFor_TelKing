<template>
    <main>
        <appOverview></appOverview>
        <appEcharts></appEcharts>
    </main>
</template>

<script>
    import Overview from './Overview/Overview.vue';
    import Echarts from './Echarts/Echarts.vue';

    export default {
        components: {
            appOverview: Overview,
            appEcharts: Echarts
        }
    }
</script>

<style scoped>
    main {
        background-color: #f5f8f9;
    }
</style>
