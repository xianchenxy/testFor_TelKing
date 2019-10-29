<template>
    <div class="ec-line"></div>
</template>

<script>
    export default {
        data() {
            return {
                ec_line_data: null
            }
        },
        beforeCreate() {
            const promise = new Promise((res, rej) => {
                const xhr = new XMLHttpRequest();
                const url = 'https://edu.telking.com/api/?type=month';
                xhr.open('get', url);
                xhr.timeout = 3000;
                xhr.ontimeout = function () {
                    alert('request timeout!');
                };
                xhr.onreadystatechange = function () {
                    if (xhr.readyState === 4) {
                        if (xhr.status >= 200 && xhr.status < 300 || xhr.status === 304) {
                            res(JSON.parse(xhr.responseText));
                        } else {
                            rej('request error');
                        }
                    }
                };
                xhr.send();
            });
            promise.then(data => {
                this.ec_line_data = data.data;
                // console.log(this.ec_line_data);
                const line_echarts = echarts.init(document.getElementsByClassName('ec-line')[0]);
                const options = {
                    title: {
                        text: '曲线图数据展示',
                        left: 'center'
                    },
                    yAxis: {
                        type: 'value',
                        axisLabel: {
                            formatter(val) {
                                return val + '人';
                            }
                        }
                    },
                    xAxis: {
                        type: 'category',
                        data: this.ec_line_data.xAxis
                    },
                    series: [
                        {
                            name: 'line-example',
                            type: 'line',
                            smooth: true,
                            data: this.ec_line_data.series,
                            label: {
                                show: true
                            },
                            itemStyle: {
                                color: '#4587f0'
                            },
                            areaStyle: {
                                color: '#f2f5fc'
                            }
                        }
                    ]
                };
                line_echarts.setOption(options);
            }, err => {
                console.log(err);
            })
        }
    }
</script>

<style scoped>
    .ec-line {
        height: 35rem;
        padding-top: 3.5rem;
        padding-bottom: 3rem;
        margin-bottom: 2rem;
        -webkit-box-sizing: border-box;
        -moz-box-sizing: border-box;
        box-sizing: border-box;
        background-color: #fff;
    }
</style>
