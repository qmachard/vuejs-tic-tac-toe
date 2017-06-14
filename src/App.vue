<template>
    <div>
        <div id="app">
            <div id="details">
                <h1>Tic Tac Toe</h1>
                <h2>Match #{{ matches + 1 }}</h2>
            </div>
            <grid></grid>
            <button class="restart" @click="restart">Restart</button>
        </div>
        <div class="scoreBoard">
            <h2>Score Board</h2>
            <div><span>O</span> : {{ wins.O }}</div>
            <div><span>X</span> : {{ wins.X }}</div>
        </div>
    </div>
</template>

<script>
    import Grid from './components/Grid.vue'
    export default {
        components: { Grid },
        name: 'app',
        data () {
            return {
                matches: 0,
                wins: {
                    O: 0,
                    X: 0
                }
            }
        },
        methods: {
            restart () {
                Event.$emit('clearCell')
                Event.$emit('gridReset')
                this.matches++
            }
        },
        created () {
            Event.$on('win', winner => this.wins[winner]++)
        }
    }
</script>

<style>
    body {
        background-color: #fff;
        color: #fff;
        font-family: 'Dosis', Helvetica, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        margin: 0px;
    }
    #app {
        margin: 0 auto;
        max-width: 270px;
        color: #34495e;
    }
    h1 {
        text-transform: uppercase;
        font-weight: bold;
        font-size: 3em;
    }
    .restart {
        background-color: #e74c3c;
        color: #fff;
        border: 0px;
        border-bottom-left-radius: 10px;
        border-bottom-right-radius: 10px;
        font-family: 'Dosis', Helvetica, sans-serif;
        font-size: 1.4em;
        font-weight: bold;
        margin: 0px;
        padding: 15px;
        width: 100%;
    }
    .restart:hover {
        background-color: #c0392b;
        cursor: pointer;
    }
    .scoreBoard {
        width: 270px;
        background-color: #EEEEEE;
        border-radius: 10px;
        box-shadow: 10px 10px #fff;
        overflow-x: hidden;
        margin: 10px auto 20px;
    }
    .scoreBoard h2 {
        margin: 0px;
        background-color: #16a085;
        padding: 10px;
    }
    .scoreBoard div {
        box-sizing: border-box;
        float: left;
        width: 50%;
        font-size: 1.5em;
        font-weight: bold;
        padding: 10px 20px;
        color: #333;
    }

    .scoreBoard div span {
        font-family: 'Gochi Hand', sans-serif;
        font-size: 1.6em;
        font-weight: bold;
        color: #16a085;
    }
</style>