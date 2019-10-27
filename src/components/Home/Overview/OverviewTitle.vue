<template>
    <section>
        <h1>Audience Overview</h1>
        <nav class="ov-btn">
            <p>Roseville, CA</p>
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
    h1 {
        font-size: 3rem;
    }

    p {
        float: left;
        font-size: 1.5rem;
    }

    .ov-btn {
        width: 100%;
        overflow: hidden;
    }

    nav {
        display: inline-block;
        font-size: 1.3rem;
    }

    ul {
        float: right;
        font-weight: bold;
    }

    li {
        float: left;
        margin-right: 3.5rem;
        cursor: pointer;
    }

    li:hover {
        color: #f40;
    }

    .cur {
        color: #f40;
        border-bottom: .2rem solid #ccc;
    }
</style>
