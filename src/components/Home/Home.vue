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
        max-width: 792px;
        padding: 0 104px;
        margin: 45px auto;
        /*background-color: #ccc;*/
    }
</style>
