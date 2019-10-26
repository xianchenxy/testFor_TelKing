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
        font-size: 1.2rem;
        text-align: center;
        background-color: #fff;
        color: #fff;
    }

    .container {
        max-width: 792px;
        margin: 0 auto;
        padding: 15px 104px;
        overflow: hidden;
    }

    .logo {
        float: left;
        width: 75px;
        height: 23px;
        line-height: 23px;
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
        width: 14px;
        height: 14px;
        background: url("../../assets/icon.png");
        -webkit-background-size: cover;
        background-size: cover;
        cursor: pointer;
    }

    .sys-btn > span:first-of-type {
        margin-right: 14px;
    }

    .sys-btn > span:last-of-type {
        background-position-x: -50%;
        margin-right: 20px;
    }

    .log-out {
        float: right;
        width: 79px;
        height: 30px;
        line-height: 30px;
        -webkit-border-radius: 5px;
        -moz-border-radius: 5px;
        border-radius: 5px;
        background-color: #f92525;
        cursor: pointer;
    }

</style>
