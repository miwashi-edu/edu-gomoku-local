# edu-gomoku-local

> We test requirements from mockup.
>
> The tests can be run with **npm test**, or **npm run test:watch**

## Instructions 

```bash
cd ~
cd ws
cd gomoku-lab
touch ./src/__tests__/mockup_tests.js
```

## ./src/gomoku.js

> This is minimum level for tests on previous level to go trough.

```bash
cat > ./src/game.js << EOFconst isTie = () => {}
const isWin = () => {}
const createBoard = () => {}
const play = () => {}

module.exports = {play, isTie, isWin, createBoard}
EOF
```

## ./src/\_\_tests\_\_/mockup_tests.js

> These are the json we found in the mockup.

```bash
cat > ./src/__tests__/mockup_tests.js << EOF
const gomokuHandler = require('../gomoku');
const gameHandler = require('../game');
const ERR_MSGS = require('../error_messages');

describe('given a gomokuHandler', () => {
    describe('when creating board', () => {
      it('should have expected properties', () => {
        const board = gomokuHandler.createBoard();
        expect(board).toHaveProperty('minInRow');
        expect(board).toHaveProperty('cols');
        expect(board).toHaveProperty('rows');
        expect(board).toHaveProperty('state');
        expect(board).toHaveProperty('tiles');
        expect(Array.isArray(board.tiles)).toBe(true);
        for( const row of board.tiles){
          expect(Array.isArray(row)).toBe(true);
          for( const tile of row){
            expect(tile).toBe(0);
          }
        }
      });
   });
});

describe('given a gameHandler', () => {
    describe('when creating game', () => {
      it('should have expected properties', () => {
        const game = gameHandler.createGame();
        expect(game).toHaveProperty("id");
        expect(game).toHaveProperty("name");
        expect(game).toHaveProperty("round");
        expect(game).toHaveProperty("player");
        expect(game).toHaveProperty("player1");
        expect(game).toHaveProperty("player2");
        expect(game).toHaveProperty("state");
        expect(game).toHaveProperty("board");
      });
    });
});
EOF
```

## Test it

> Try solving all requirements, soluting will be shown in next level.

```bash
npm test
```
