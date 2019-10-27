<template>
    <header>
        <div class="container">
            <div class="logo" onclick="window.location.reload()">LOGO</div>
            <div class="log-out" onclick="alert('退出成功！')">Log Out</div>
            <div class="sys-btn">
                <span title="设置"></span><span title="消息"></span>
            </div>
        </div>
    </header>
</template>

<script>
    export default {
        name: ""
    }
</script>

<style scoped>
    header {
        top: 0;
        position: fixed;
        width: 100%;
        font-size: 1.2rem;
        text-align: center;
        background-color: #fff;
        color: #fff;
        z-index: 999;
    }

    .container {
        max-width: 114rem;
        margin: 0 auto;
        /*padding: 3rem 15rem;*/
        padding: 3rem 0;
        overflow: hidden;
    }

    .sys-btn {
        height: 2rem;
        margin-top: 1.1rem;
        float: right;
    }

    .sys-btn > span {
        display: inline-block;
        width: 2rem;
        height: 2rem;
        background: url("../../assets/img/icon.png");
        -webkit-background-size: cover;
        background-size: cover;
        cursor: pointer;
    }

    .sys-btn > span:first-of-type {
        margin-right: 1.4rem;
    }

    .sys-btn > span:last-of-type {
        background-position-x: -50%;
        margin-right: 2rem;
    }

    .log-out {
        float: right;
        width: 11.2rem;
        height: 4.2rem;
        line-height: 4.2rem;
        -webkit-border-radius: .5rem;
        -moz-border-radius: .5rem;
        border-radius: .5rem;
        background-color: #f92525;
        cursor: pointer;
    }

    .log-out:hover {
        opacity: .8;
    }
</style>
