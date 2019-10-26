<template>
    <section>
        <div class="ov-info">
            <h1>Audience Overview</h1>
            <p>Roseville, CA</p>
        </div>
        <nav class="ov-btn">
            <ul @click="toFocus($event)" ref="btns">
                <li v-for="(btn, ind) in btnData" :class="{'cur': cur === ind}">{{ btn }}</li>
            </ul>
        </nav>
    </section>
</template>

<script>
    export default {
        data() {
            return {
                btnData: ['DASHBOARD', 'PROJECTS', 'CALENDAR', 'MAILBOX', 'SETTINGS'],
                cur: 0,
                childs: ''
            }
        },
        methods: {
            toFocus(ev) {
                if (ev.target.localName === 'li') {
                    if (!this.childs)
                        this.childs = this.$refs['btns'].children;
                    this.childs[this.cur].classList.remove('cur');
                    this.cur = Array.prototype.indexOf.call(this.childs, ev.target);
                }
            }
        }
    }
</script>

<style scoped>
    section {
        overflow: hidden;
        /*background: lightblue;*/
    }

    .ov-info {
        float: left;
    }

    h1 {
        font-size: 3rem;
    }

    p {
        font-size: 1.5rem;
    }

    .ov-btn {
        float: right;
        position: relative;
        top: 40px;
        overflow: hidden;
        /*background: lavender;*/
    }

    nav {
        display: inline-block;
        font-size: 1.3rem;
    }

    li {
        float: left;
        margin-right: 35px;
        cursor: pointer;
    }

    .cur {
        color: #f40;
        border-bottom: 2px solid #ccc;
    }
</style>
