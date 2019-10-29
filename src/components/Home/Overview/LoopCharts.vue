<template>
    <div class="loop-chart">
        <ul class="charts" ref="chart_box" :style="switchCharts">
            <li v-for="(pic, ind) in pics" :style="initStyle(pic)" :title="'轮播图' + (ind + 1)"></li>
        </ul>
        <aside>
            <span class="to-left" @click="updChartIndex('-1', true)"><</span>
            <span class="to-right" @click="updChartIndex('1', true)">></span>
            <ul class="charts-index">
                <li v-for="ind in pics.length" @click="updChartIndex(ind, true)"
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
                chart_box: null,
                timer: null,
                chartTime: 3000,   //轮播间隔
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
            updChartIndex(ind, isUserClick) {
                //为避免轮播图的定时滚动和用户行为点击造成【多次点击】的现象，
                //每次用户行为点击后，需要重启定时器
                if (isUserClick) {
                    this.closeLoopChart(this);
                    this.startLoopChart(this);
                }

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
            },
            startLoopChart(vm) {
                if (!vm || !vm._isVue)  //为空 or 非Vue实例
                    throw new Error('the param requires a Vue Instance!');
                this.timer = setInterval(function () {
                    // console.log('loop');
                    vm.updChartIndex('1');  //不可用数字1，会被判以为点击的是索引方块
                }, this.chartTime);
            },
            closeLoopChart(vm) {
                clearInterval(vm.timer);
            }
        },
        mounted() {
            const _vm = this;
            //开启定时轮播
            this.startLoopChart(_vm);
            //鼠标悬停时关闭定时器，离开则重启
            this.$refs['chart_box'].addEventListener('mouseenter', () => {
                _vm.closeLoopChart(_vm)
            }, false);
            this.$refs['chart_box'].addEventListener('mouseleave', () => {
                _vm.startLoopChart(_vm);
            }, false);
        }
    }
</script>

<style scoped>
    .loop-chart,
    ul.charts li {
        float: left;
        width: 54rem;
        height: 26.8rem;
    }

    .loop-chart {
        position: relative;
        margin-top: 5rem;
        border: 1rem solid #fff;
        overflow: hidden;
    }

    ul.charts {
        position: absolute;
        width: 1000rem;
        -webkit-transition: all 1s;
        -moz-transition: all 1s;
        -ms-transition: all 1s;
        -o-transition: all 1s;
        transition: all 1s;
    }

    ul.charts li {
        -webkit-background-size: cover !important;
        background-size: cover !important;
    }

    aside > * {
        position: absolute;
    }

    aside > span {
        display: inline-block;
        width: 2.5rem;
        height: 3.5rem;
        line-height: 3.5rem;
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
        font-size: 1.6rem;
        color: #fff;
        background-color: #03050d;
        cursor: pointer;
    }

    .to-left {
        left: 0;
        margin-left: .5rem;
    }

    .to-right {
        right: 0;
        margin-right: .5rem;
    }

    aside > span:hover {
        background-color: #333;
    }

    ul.charts-index {
        left: 50%;
        bottom: .5rem;
        -webkit-transform: translate(-50%, 0) rotate(180deg);
        -moz-transform: translate(-50%, 0) rotate(180deg);
        -ms-transform: translate(-50%, 0) rotate(180deg);
        -o-transform: translate(-50%, 0) rotate(180deg);
        transform: translate(-50%, 0) rotate(180deg);
        /*background: lightskyblue;*/
    }

    ul.charts-index > li {
        float: left;
        width: .8rem;
        height: 1rem;
        margin: 0 .4rem;
        -webkit-transition: height 400ms;
        -moz-transition: height 400ms;
        -ms-transition: height 400ms;
        -o-transition: height 400ms;
        transition: height 400ms;
        background-color: #8d9498;
        cursor: pointer;
    }

    ul.charts-index > li:hover {
        height: 1.4rem;
    }

    li.cur {
        height: 1.4rem !important;
    }
</style>
