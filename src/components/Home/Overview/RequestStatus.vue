<template>
    <div class="req-status">
        <div class="title">
            <div class="title-name">
                <h3>{{ title_name }}</h3>
            </div>
            <div class="title-btn">View All</div>
        </div>
        <div class="wrapper">
            <div class="wrap-title">
                <ul>
                    <li v-for="title in wrapp_title">{{ title }}</li>
                </ul>
            </div>
            <div class="wrap-body">
                <ul v-for="data in sup_req">
                    <li v-for="info in data">{{ info }}</li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                title_name: 'Support Request',
                wrapp_title: ['Time', 'user name', 'Status'],
                sup_req: [
                    {time: '9:45pm', userName: 'info@design.com', status: 'Sovled'},
                    {time: '9:45pm', userName: 'info@design.com', status: 'Sovled'},
                    {time: '9:45pm', userName: 'info@design.com', status: 'Sovled'},
                    {time: '9:45pm', userName: 'info@design.com', status: 'Sovled'}
                ]
            }
        }
    }
</script>

<style scoped>
    .req-status {
        float: right;
        width: 390px;
        height: 200px;
        background-color: #fff;
        overflow: hidden;
    }

    .title {
        padding: 20px 36px;
        height: 34px;
        border-bottom: 1px solid #eaeaea;
    }

    .title-name {
        float: left;
        font-size: 1.8rem;
        cursor: default;
    }

    .title-btn {
        float: right;
        padding: 7px 10px;
        font-size: 1.3rem;
        border: 1px solid #eaeaea;
        cursor: pointer;
    }

    .title-btn:hover {
        color: #f40;
    }

    .wrapper {
        padding: 0 36px;
        overflow: hidden;
        /*background-color: lightskyblue;*/
    }

    .wrapper ul {
        font-size: 1.3rem;
        margin-bottom: 7px;
        /*background-color: lavender;*/
        overflow: hidden;
    }

    .wrapper .wrap-title > ul:first-of-type {
        font-size: 1.4rem;
    }

    .wrapper ul > li {
        float: left;
        padding: 6px;
    }

    .wrapper ul > li:first-of-type {
        width: 72px;
    }

    .wrapper ul > li:last-of-type {
        float: right;
    }

    .wrap-title {
        position: relative;
        padding-top: 16px;
        z-index: 1;
        background-color: #fff;
    }

    .wrapper .wrap-body > ul > li:last-of-type {
        background-color: #5dd054;
        color: #fff;
    }

    .wrap-body {
        position: relative;
        top: 0;
        -webkit-transition: top 1s;
        -moz-transition: top 1s;
        -ms-transition: top 1s;
        -o-transition: top 1s;
        transition: top 1s;
    }
</style>
