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
    .overview {
        max-width: 114rem;
        margin: 0 auto;
        /*padding: 7rem 15rem 2rem;*/
        padding: 7rem 0 2rem;
        overflow: hidden;
    }

    section {
        /*margin-top: 3.5rem;*/
        overflow: hidden;
    }
</style>
