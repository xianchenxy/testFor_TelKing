<template>
    <article class="overview">
        <appOverviewTitle></appOverviewTitle>
        <section>
            <appLoopCharts></appLoopCharts>
            <appRequestStatus></appRequestStatus>
        </section>
    </article>
</template>

<script>
    import OverviewTitle from './OverviewTitle.vue'
    import LoopCharts from './LoopCharts.vue'
    import RequestStatus from './RequestStatus.vue'

    export default {
        components: {
            appOverviewTitle: OverviewTitle,
            appLoopCharts: LoopCharts,
            appRequestStatus: RequestStatus
        }
    }
</script>

<style scoped>
    section  {
        margin-top: 35px;
        overflow: hidden;
    }
</style>
