<template>
    <table class="grid">
        <tr>
            <Cell name="1"></Cell>
            <Cell name="2"></Cell>
            <Cell name="3"></Cell>
        </tr>
        <tr>
            <Cell name="4"></Cell>
            <Cell name="5"></Cell>
            <cell name="6"></cell>
        </tr>
        <tr>
            <Cell name="7"></Cell>
            <Cell name="8"></Cell>
            <Cell name="9"></Cell>
        </tr>
    </table>
</template>

<script>
    import Cell from './Cell.vue';

    export default {
        components: { Cell },
        data () {
            return {
                // can be O or X
                activePlayer: 'O',
                // maintains the status of the game: turn or win or draw
                gameStatus: 'turn',

                gameStatusMessage: `O's turn`,
                // status color is used as background color in the status bar
                // it can hold the name of either of the following CSS classes
                // statusTurn (default) is yellow for a turn
                // statusWin is green for a win
                // statusDraw is purple for a draw
                gameStatusColor: 'statusTurn',
                // no. of moves played by both players in a single game (max = 9)
                moves: 0,
                // stores the placement of X and O in cells by their cell number
                cells: {
                    1: '', 2: '', 3: '',
                    4: '', 5: '', 6: '',
                    7: '', 8: '', 9: ''
                },
                // contains all (8) possible winning conditions
                winConditions: [
                    [1, 2, 3], [4, 5, 6], [7, 8, 9], // rows
                    [1, 4, 7], [2, 5, 8], [3, 6, 9], // columns
                    [1, 5, 9], [3, 5, 7]             // diagonals
                ],
            }
        }
    }
</script>

<style>
    .grid {
        background-color: #34495e;
        color: #fff;
        width: 100%;
        border-collapse: collapse;
    }

    .gameStatus {
        margin: 0px;
        padding: 15px;
        border-top-left-radius: 20px;
        border-top-right-radius: 20px;
        background-color: #f1c40f;
        color: #fff;
        font-size: 1.4em;
        font-weight: bold;
    }

    .statusTurn {
        background-color: #f1c40f;
    }

    .statusWin {
        background-color: #2ecc71;
    }

    .statusDraw {
        background-color: #9b59b6;
    }
</style>