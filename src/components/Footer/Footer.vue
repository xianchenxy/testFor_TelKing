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
        bottom: 0;
        position: fixed;
        width: 100%;
        /*padding: 8rem 15rem;*/
        padding: 8rem 0;
        background-color: #202124;
        -webkit-box-sizing: border-box;
        -moz-box-sizing: border-box;
        box-sizing: border-box;
        color: #fff;
        z-index: 1;
    }

    aside {
        position: relative;
        max-width: 114rem;
        margin: 0 auto;
        font-size: 1.3rem;
        /*background-color: lightskyblue;*/
    }

    aside nav {
        display: inline-block;
        width: 16.5%;
    }

    aside nav:first-of-type,
    aside nav:last-of-type {
        vertical-align: top;
    }

    ul {
        display: inline-block;
    }

    ul > li {
        margin-bottom: 1.9rem;
        cursor: pointer;
    }

    aside nav > ul > li:last-of-type {
        margin-bottom: 0;
    }

    li:hover {
        color: #f40;
        text-decoration: underline;
    }

    .underline {
        text-decoration: underline;
    }
</style>
