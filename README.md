# edu-gomoku-local

> We crete a project for laborating with requirements for gomoku. We set up the project with jest testing framework with source code in src directory and tests
> in src/\_\_tests\_\_ directory, which is a default folder for jest to find its tests.
> We also create a test_util.js and error_message.js. Normally these are created during coding, but
> as we want to focus on test first development these will be given.
>
> The tests can be run with **npm test**, or **npm run test:watch**

## Instructions 

```bash
cd ~
cd ws
mkdir gomoku-local
cd gomoku-local
npm init -y
npm pkg set scripts.test="jest"
npm pkg set scripts.test:watch="jest --watchAll"
npm install dotenv
npm install -D jest
mkdir -p src/__tests__
touch ./src/{gomoku.js,error_messages.js,test_utils.js}
touch ./__tests__/gomoku_tests.js
```

## ./src/test_utils.js

> Test utilites that will help us test game functionality.

```bash
cat > ./src/test_utils.js << EOF
const randomSquare = ({cols, rows}) => ({
    col: Math.floor(Math.random() * cols) + 1,
    row: Math.floor(Math.random() * rows) + 1
  });
  
  const randomSequence = ({cols, rows, minInRow}, dx, dy) => {
    const col = Math.floor(Math.random() * (cols - minInRow + 1)) + 1;
    const row = Math.floor(Math.random() * (rows - minInRow + 1)) + 1;
    return Array.from({length: minInRow}, (_, i) => ({col: col + i * dx, row: row + i * dy}));
  }
  
  const randomDiagonal = (board) => randomSequence(board, 1, 1);
  const randomHorisontal = (board) => randomSequence(board, 1, 0);
  const randomVertical = (board) => randomSequence(board, 0, 1);
  
  const fillBoard = (board) => {
    let player = 1;
    for (let col = 0; col < board.tiles.length; col++) {
      for (let row = 0; row < board.tiles[col].length; row++) {
        board.tiles[col][row] = player;
        player = 3 - player; // Alternate between 1 and 2
      }
    }
    return board;
  }
  
  module.exports = { randomSquare, randomVertical, randomHorisontal, randomDiagonal, fillBoard };
EOF
```

## ./src/error_messages.js

> Error messages used in the whole system

```bash
cat > ./src/error_messages.js << EOF
const ERR_TILE_OUT_OF_BOUNDS="Tile don't exist!";
const ERR_TILE_OCCUPIED="Tile occupied!";
const ERR_PLAYER_OUT_OF_TURN="Player out of turn!";
const ERR_GAME_FULL="Game is full!";
const ERR_GAME_NOT_FOUND="Game not found!";
const ERR_INVALID_PLAYER_ID="Invalid player ID!";
const ERR_PLAYER_NOT_FOUND="Player not found!";

module.exports = {
    ERR_TILE_OCCUPIED,
    ERR_TILE_OUT_OF_BOUNDS,
    ERR_PLAYER_OUT_OF_TURN,
    ERR_GAME_FULL,
    ERR_GAME_NOT_FOUND,
    ERR_INVALID_PLAYER_ID,
    ERR_PLAYER_NOT_FOUND
};
EOF
```

## ./src/__tests__/gomoku_tests.js

> This is the file where we will write our tests.

```bash
cat > ./src/__tests__/gomoku_tests.js << EOF
//Dummy test to show jest is working
describe('jest', () => {
    describe('component test', () => {
      it('should work', () => {
        expect(1).toBe(1);
      });
    });
});
EOF
```

## Test it

```bash
npm test
```
