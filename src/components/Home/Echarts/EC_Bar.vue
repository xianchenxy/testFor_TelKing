<template>
    <div class="ec-bar"></div>
</template>

<script>
    export default {
        props: ['bar_data'],
        watch: {
            bar_data() {
                const bar_echarts = echarts.init(document.getElementsByClassName('ec-bar')[0]);
                const options = {
                    title: {
                        text: '柱状图数据展示',
                        left: 'center'
                    },
                    xAxis: {
                        type: 'category',
                        data: this.bar_data.xAxis
                    },
                    yAxis: {
                        type: 'value',
                        name: '商品数',
                    },
                    series: [
                        {
                            name: 'bar-example',
                            type: 'bar',
                            data: this.bar_data.series,
                            center: ['50%', '60%'],
                            itemStyle: {
                                color: '#4587f0'
                            },
                            barWidth: '25%'
                        }
                    ],
                    grid: {
                        bottom: 20
                    }
                };
                bar_echarts.setOption(options);
            }
        }
    }
</script>

<style scoped>
    .ec-bar {
        float: right;
        width: 56rem;
        height: 37.7rem;
        padding: 3.1rem;
        -webkit-box-sizing: border-box;
        -moz-box-sizing: border-box;
        box-sizing: border-box;
        background-color: #fff;
    }
</style>
