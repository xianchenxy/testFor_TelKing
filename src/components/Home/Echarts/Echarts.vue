<template>
    <article class="e-charts">
        <section>
            <appEC_Line></appEC_Line>
        </section>
        <section style="overflow: hidden;">
            <appEC_Pie :pie_data="ec_BarPie_data"></appEC_Pie>
            <appEC_Bar :bar_data="ec_BarPie_data"></appEC_Bar>
        </section>
    </article>
</template>

<script>
    import EC_Line from './EC_Line.vue'
    import EC_Bar from './EC_Bar.vue'
    import EC_Pie from './EC_Pie.vue'

    export default {
        data() {
            return {
                ec_BarPie_data: null
            }
        },
        components: {
            appEC_Line: EC_Line,
            appEC_Bar: EC_Bar,
            appEC_Pie: EC_Pie
        },
        beforeCreate() {
            const promise = new Promise((res, rej) => {
                const xhr = new XMLHttpRequest();
                const url = 'https://edu.telking.com/api/?type=week';
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
                this.ec_BarPie_data = data.data;
            }, err => {
                console.log(err);
            })
        }
    }
</script>

<style scoped>
    .e-charts {
        width: 114rem;
        margin: 0 auto;
    }
</style>
