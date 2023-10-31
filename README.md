# edu-gomoku-local

> We test requirements from mockup.
>
> The tests can be run with **npm test**, or **npm run test:watch**

## Instructions 

```bash
cd ~
cd ws
cd gomoku-lab
npm install uuid
```

## ./src/gomoku.js

> This is minimum level for tests on previous level to go trough.

```bash
cat > ./src/gomoku.js << EOF
const MINIMUM_WIN_LENGTH = 5;
const DEFAULT_COLS = 16;
const DEFAULT_ROWS = DEFAULT_COLS;

const COLS = process.env.COLS || DEFAULT_COLS;
const ROWS = process.env.ROWS || DEFAULT_ROWS;


const isTie = () => {}
const isWin = () => {}

const createBoard = () => {
    const board = {
        minInRow: MINIMUM_WIN_LENGTH,
        cols: COLS,
        rows: ROWS,
        tiles: []
    }
    for (let i = 0; i < COLS + 1; i++) {
        board.tiles.push(Array(ROWS + 1));
    }
    for(let col = 0; col <= board.tiles.length - 1; col++){
        for(let row = 0; row <= board.tiles.length - 1; row++){
                board.tiles[col][row] = 0;
        }
    }
    return board;
}

const play = () => {}

module.exports = {play, isTie, isWin, createBoard}
EOF
```

## ./src/game.js

> This is minimum level for tests on previous level to go trough.

```bash
cat > ./src/game.js << EOF
const uuid = require('uuid');
const gomokuHandler = require('./gomoku.js');

let numGames = 0;

const play = () => {}
const createGame = (name) => {
    if(!name){
        name = "game_" + numGames++;
    }
    const board = gomokuHandler.createBoard()
    const game = {
        id: uuid.v4(),
        name: name,
        round: 0,
        player: 0,
        player1: null,
        player2: null,
        board: board,
        state: board.state
    };
    return game;
}

const listGames = () => {}
const findGameById = () => {}
const addPlayer = () => {}

module.exports = {play,createGame,listGames,findGameById,addPlayer}
EOF
```
