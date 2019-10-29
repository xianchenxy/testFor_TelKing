<template>
    <div class="ec-pie"></div>
</template>

<script>
    export default {
        props: ['pie_data'],
        watch: {
            pie_data() {
                const pie_echarts = echarts.init(document.getElementsByClassName('ec-pie')[0]);
                const series_pie = [];
                for (let i in this.pie_data.xAxis) {
                    series_pie.push({
                        name: this.pie_data.xAxis[i],
                        value: this.pie_data.series[i]
                    })
                }
                // console.log(series_pie);
                const options = {
                    title: {
                        text: '饼状图数据展示',
                        left: 'center'
                    },
                    series: [
                        {
                            name: 'pie-example',
                            type: 'pie',
                            data: series_pie,
                            center: ['50%', '60%']
                        }
                    ]
                };
                pie_echarts.setOption(options);
            }
        }
    }
</script>

<style scoped>
    .ec-pie {
        float: left;
        width: 56rem;
        height: 37.7rem;
        padding: 3.1rem;
        -webkit-box-sizing: border-box;
        -moz-box-sizing: border-box;
        box-sizing: border-box;
        background-color: #fff;
    }
</style>
