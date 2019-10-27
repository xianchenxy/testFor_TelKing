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
        width: 56rem;
        height: 28.8rem;
        margin-top: 5rem;
        background-color: #fff;
        overflow: hidden;
    }

    .title {
        padding: 4rem 5rem 2.9rem;
        border-bottom: 2px solid #f5f8f9;
        overflow: hidden;
    }

    .title-name {
        float: left;
        font-size: 1.8rem;
        cursor: default;
    }

    .title-btn {
        float: right;
        padding: 1.3rem 2rem;
        font-size: 1.3rem;
        border: 2px solid #eaeaea;
        cursor: pointer;
    }

    .title-btn:hover {
        color: #f40;
    }

    .wrapper {
        padding: 0 5rem;
        overflow: hidden;
        /*background-color: lightskyblue;*/
    }

    .wrapper ul {
        font-size: 1.3rem;
        margin-bottom: 1.5rem;
        /*background-color: lavender;*/
        overflow: hidden;
    }

    .wrapper ul > li {
        float: left;
        padding: 1rem 0;
    }

    .wrapper ul > li:first-of-type {
        width: 7.2rem;
    }

    .wrapper ul > li:last-of-type {
        float: right;
        padding: 1rem 1.2rem;
        background-color: #5dd054;
        color: #fff;
    }

    .wrap-title {
        position: relative;
        padding-top: 1.5rem;
        background-color: #fff;
        z-index: 1;
    }

    .wrapper .wrap-title > ul:first-of-type {
        font-size: 1.4rem;
    }

    .wrapper .wrap-title > ul > li {
        font-weight: bold;
    }

    .wrapper .wrap-title > ul > li:last-of-type {
        font-weight: normal;
        background-color: #fff;
        color: #000;
    }

    .wrap-body {
        position: relative;
        top: 0;
        /*top: -100px;*/
        -webkit-transition: top 1s;
        -moz-transition: top 1s;
        -ms-transition: top 1s;
        -o-transition: top 1s;
        transition: top 1s;
    }
</style>
