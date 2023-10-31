# edu-gomoku-local

> We test gomoku.js
>
> The tests can be run with **npm test**, or **npm run test:watch**

## Instructions 

```bash
cd ~
cd ws
cd gomoku-lab
```

## ./src/\_\_tests\_\_/gomoku_tests.js

> Turn on test one by one and fullfill the requirements.

```bash
cat > ./src/__tests__/gomoku_tests.js << EOF
/**
 * @group unit
 */

const gomokuHandler = require('../gomoku.js');
const ERR_MSGS = require('../error_messages.js');
const testUtil = require('../test_utils.js');

  /**
   * Test if a tile gets occupied with play.
   */
  describe.skip('given a board, and tile', () => {
    const player = 1;
    const row = 1; 
    const col = 1;
    let board = gomokuHandler.createBoard();
    describe('when playing the tile', () => {
      board = gomokuHandler.play(board, row, col, player);
      it('tile should be occupied', () => {
        expect(
          board.tiles[row][col]
        ).toBe(player);
      });
    });
  });
  
  /**
   * Test if playing first and last tile works.
   * This test is important as it will test the boundaries
   * does first tile start with 0 or 1?
   */
  describe.skip('given a board, and player', () => {
    const player = 1;
    let board = gomokuHandler.createBoard();
    describe('when playing outside board', () => {
      it('last tile should not throw exception', () => {
        expect(() => {
          gomokuHandler.play(board, board.cols, board.rows, player);
        }).not.toThrow("Tile don't exist!")
      });
      it('first tile should not throw exception', () => {
        expect(() => {
          gomokuHandler.play(board, 1, 1, player);
        }).not.toThrow(ERR_MSGS.ERR_TILE_OUT_OF_BOUNDS)
      });
    })
  });

  /**
   * Test if playing outside board throws Exception
   */
  describe.skip('given a board, and player', () => {
    const player = 1;
    let board = gomokuHandler.createBoard();
    describe('when playing outside board', () => {
      describe('to left', () => {
        it('should throw exception', () => {
          expect(() => {
            gomokuHandler.play(board, 0, 1, player);
          }).toThrow(ERR_MSGS.ERR_TILE_OUT_OF_BOUNDS)
        });
      });

      describe('to right', () => {
        it('should throw exception', () => {
          expect(() => {
            gomokuHandler.play(board, board.cols + 1, 1, player);
          }).toThrow(ERR_MSGS.ERR_TILE_OUT_OF_BOUNDS)
        });
      });

      describe('above', () => {
        it('should throw exception', () => {
          expect(() => {
            gomokuHandler.play(board, board.cols + 1, 1, player);
          }).toThrow(ERR_MSGS.ERR_TILE_OUT_OF_BOUNDS)
        });
      });

      describe('below', () => {
        it('should throw exception', () => {
          expect(() => {
            gomokuHandler.play(board, board.cols + 1, 1, player);
          }).toThrow(ERR_MSGS.ERR_TILE_OUT_OF_BOUNDS)
        });
      });

    });
  });

  /**
   * Test if playing on same tile throws Exception
   */
  describe.skip('given a board, and tile', () => {
    const player = 1;
    const tile = {col: 1, row: 1};
    let board = gomokuHandler.createBoard();
    describe('when playing on non empty tile', () => {
      board = gomokuHandler.play(board, tile.col, tile.row, player);
      it('game should throw exception', () => {
        expect(() => {
          gomokuHandler.play(board, tile.col, tile.row, player);
        }).toThrow(ERR_MSGS.ERR_TILE_OCCUPIED)
      });
    });
  });

  /**
   * Test if a gameHandler can detect that no winner exists!
   */
  describe.skip('given an empty board', () => {
    let board = gomokuHandler.createBoard();
    describe('when checking for win condition', () => {
      it('isWin should return false', () => {
        expect(gomokuHandler.isWin(board)).toBe(false);
      });
    });
  });

  /**
   * Test if gameHandler can detect that a winner does exist
   */
  describe.skip('given a board', () => {
    const  player = 1;

    describe('when having random diagonal five in row', () => {
      let board = gomokuHandler.createBoard();
      for(let tile of testUtil.randomDiagonal(board)){
        board = gomokuHandler.play(board, tile.col, tile.row, player);
      }
      it('isWin should return true', () => {
        expect(gomokuHandler.isWin(board)).toBe(true);
      });
    });

    describe('when having random vertical five in row', () => {
      let board = gomokuHandler.createBoard();
      for(let tile of testUtil.randomVertical(board)){
        board = gomokuHandler.play(board, tile.col, tile.row, player);
      }
      it('isWin should return true', () => {
        expect(gomokuHandler.isWin(board)).toBe(true);
      });
    });

    describe('when having random horizontal five in row', () => {
      let player = 1;
      let board = gomokuHandler.createBoard();
      for(let tile of testUtil.randomHorisontal(board)){
        board = gomokuHandler.play(board, tile.col, tile.row, player);
      }
      it('isWin should return true', () => {
        expect(gomokuHandler.isWin(board)).toBe(true);
      });
    });
  });

/**
 * Test if gameHandler can detect that a winner does exist
 */
describe.skip('given a board', () => {
  const  player = 1;
  describe('when more moves, and no winner', () => {
    let board = gomokuHandler.createBoard();
    it('isTie should return true', () => {
      expect(gomokuHandler.isTie(board)).toBe(false);
    });
  });

  describe('when no more moves, and no winner', () => {
    let board = gomokuHandler.createBoard();
    board = testUtil.fillBoard(board);
    it('isTie should return true', () => {
      expect(gomokuHandler.isTie(board)).toBe(true);
    });
  });

});
EOF
```

## Test it

```bash
npm test
```
