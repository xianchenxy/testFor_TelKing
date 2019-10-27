<template>
    <footer>
        <aside>
            <nav>
                <div class="logo" onclick="window.location.reload()">LOGO</div>
            </nav>
            <nav v-for="nav in nav_list">
                <ul>
                    <li v-for="item in nav" :class="{'underline': 'CULTURE' === item}">{{ item }}</li>
                </ul>
            </nav>
        </aside>
    </footer>
</template>

<script>
    export default {
        data() {
            return {
                nav_list: [
                    ['NEWS', 'CHANNELS', 'OVERVIEW', 'TIMELINE'],
                    ['SPORT', 'CULTURE', 'NATURE', 'MUSIC'],
                    ['WEATHER', 'AUTOS', 'LOCAL', 'SHOP'],
                    ['FUTURE', 'FOOD', 'EARTH', 'TV'],
                    ['TRAVEL', 'RADIO']
                ]
            }
        }
    }
</script>

<style scoped>
    footer {
        padding: 50px 30px 80px;
        background-color: #202124;
        color: #fff;
    }

    aside {
        position: relative;
        max-width: 792px;
        padding: 0 44px 0 100px;
        margin: 0 auto;
        font-size: 1.3rem;
        /*background-color: lightskyblue;*/
    }

    aside nav:not(:first-of-type) {
        display: inline-block;
        width: 20%;
    }

    aside nav:last-of-type {
        vertical-align: top;
    }

    .logo {
        left: 0;
        position: absolute;
        width: 75px;
        height: 23px;
        margin: 5px 0;
        line-height: 23px;
        -webkit-border-radius: 5px;
        -moz-border-radius: 5px;
        border-radius: 5px;
        text-align: center;
        font-size: 1.2rem;
        background-color: #f92525;
        cursor: pointer;
    }

    .logo:hover {
        opacity: .8;
    }

    ul {
        display: inline-block;
    }

    ul > li {
        margin: 5px 0;
        cursor: pointer;
    }

    li:hover {
        color: #f40;
        text-decoration: underline;
    }

    .underline {
        text-decoration: underline;
    }
</style>
