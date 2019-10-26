<template>
    <div class="loop-chart">
        <ul class="charts" ref="chart_box" :style="switchCharts">
            <li v-for="(pic, ind) in pics" :style="initStyle(pic)" :title="'轮播图' + (ind + 1)"></li>
        </ul>
        <aside>
            <span class="to-left" @click="updChartIndex('-1')"><</span>
            <span class="to-right" @click="updChartIndex('1')">></span>
            <ul class="charts-index">
                <li v-for="ind in pics.length" @click="updChartIndex(ind)"
                    :class="{'cur': (pics.length - nowInd) === ind}"></li>
            </ul>
        </aside>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                pics: [
                    'http://xianchenxy.cn/img/loopcharts/man1.jpeg',
                    'http://xianchenxy.cn/img/loopcharts/man2.jpeg',
                    'http://xianchenxy.cn/img/loopcharts/man3.jpeg',
                    'http://xianchenxy.cn/img/loopcharts/man4.jpeg',
                    'http://xianchenxy.cn/img/loopcharts/man5.jpeg',
                ],
                nowInd: 0,
                step: '',
                chart_box: null
            }
        },
        computed: {
            initStyle() {
                return function (src) {
                    return `background: url(${src})`;
                }
            },
            switchCharts() {
                return `left: ${-this.step * this.nowInd}px`;
            }
        },
        methods: {
            updChartIndex(ind) {
                let nowInd = this.nowInd; //此处是为了避免直接更改data值引起的不必要的更新
                const toIndex = parseFloat(ind);
                if (toIndex !== toIndex) {
                    throw new Error('请传递可转化为number类型的参数!');
                }

                if (!this.chart_box)
                    this.chart_box = this.$refs['chart_box'];
                if (!this.step)
                    this.step = parseFloat(window.getComputedStyle(this.chart_box.children[0], null).width);

                if (typeof ind === 'string') {    //点击的是按钮
                    nowInd += toIndex;
                    if (nowInd >= this.pics.length) {//处于上边界值
                        nowInd = 0;
                    } else if (nowInd < 0) { //处于下边界值
                        nowInd = this.pics.length - 1;
                    }
                } else {    //点击的是索引方块
                    nowInd = this.pics.length - ind;
                }
                // console.log(nowInd);
                this.nowInd = nowInd;
            }
        }
    }
</script>

<style scoped>
    .loop-chart {
        position: relative;
        width: 539px;
        height: 267px;
        overflow: hidden;
    }

    ul.charts {
        position: absolute;
        width: 10000px;
        -webkit-transition: all 1s;
        -moz-transition: all 1s;
        -ms-transition: all 1s;
        -o-transition: all 1s;
        transition: all 1s;
    }

    ul.charts li {
        float: left;
        width: 539px;
        height: 267px;
        -webkit-background-size: cover !important;
        background-size: cover !important;
    }

    aside > * {
        position: absolute;
    }

    aside > span {
        display: inline-block;
        width: 25px;
        height: 40px;
        line-height: 40px;
        top: 50%;
        -webkit-transform: translate(0, -50%);
        -moz-transform: translate(0, -50%);
        -ms-transform: translate(0, -50%);
        -o-transform: translate(0, -50%);
        transform: translate(0, -50%);
        -webkit-transition: all 400ms;
        -moz-transition: all 400ms;
        -ms-transition: all 400ms;
        -o-transition: all 400ms;
        transition: all 400ms;
        text-align: center;
        font-size: 2rem;
        color: #fff;
        background-color: #03050d;
        cursor: pointer;
    }

    .to-left {
        left: 0;
        margin-left: 5px;
    }

    .to-right {
        right: 0;
        margin-right: 5px;
    }

    aside > span:hover {
        background-color: #333;
    }

    ul.charts-index {
        left: 50%;
        bottom: 5px;
        -webkit-transform: translate(-50%, 0) rotate(180deg);
        -moz-transform: translate(-50%, 0) rotate(180deg);
        -ms-transform: translate(-50%, 0) rotate(180deg);
        -o-transform: translate(-50%, 0) rotate(180deg);
        transform: translate(-50%, 0) rotate(180deg);
        /*background: lightskyblue;*/
    }

    ul.charts-index > li {
        float: left;
        width: 10px;
        height: 12px;
        margin: 0 5px;
        -webkit-transition: height 400ms;
        -moz-transition: height 400ms;
        -ms-transition: height 400ms;
        -o-transition: height 400ms;
        transition: height 400ms;
        background-color: #8d9498;
        cursor: pointer;
    }

    ul.charts-index > li:hover {
        height: 20px;
    }

    li.cur {
        height: 20px !important;
    }
</style>
