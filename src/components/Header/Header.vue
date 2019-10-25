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
        padding: 0 150px;
        font-size: 1.4rem;
        text-align: center;
        background-color: #fff;
        color: #fff;
    }

    .container {
        max-width: 1140px;
        margin: 0 auto;
        padding: 30px 0;
        overflow: hidden;
    }

    .logo {
        float: left;
        width: 107px;
        height: 32px;
        line-height: 32px;
        -webkit-border-radius: 5px;
        -moz-border-radius: 5px;
        border-radius: 5px;
        background-color: #f92525;
        cursor: pointer;
    }

    .sys-btn {
        height: 20px;
        margin-top: 11px;
        float: right;
    }

    .sys-btn > span {
        display: inline-block;
        width: 20px;
        height: 20px;
        background: url("../../assets/icon.png");
        -webkit-background-size: cover;
        background-size: cover;
        cursor: pointer;
    }

    .sys-btn > span:first-of-type {
        margin-right: 20px;
    }

    .sys-btn > span:last-of-type {
        background-position-x: -50%;
        margin-right: 40px;
    }

    .log-out {
        float: right;
        width: 112px;
        height: 42px;
        line-height: 42px;
        -webkit-border-radius: 5px;
        -moz-border-radius: 5px;
        border-radius: 5px;
        background-color: #f92525;
        cursor: pointer;
    }

</style>
