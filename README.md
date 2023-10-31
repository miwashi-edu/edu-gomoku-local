# edu-gomoku-local

> We test game.js
>
> The tests can be run with **npm test**, or **npm run test:watch**

## Instructions 

```bash
cd ~
cd ws
cd gomoku-lab
npm install -D @faker-js/faker
npm install -D uuid-validate
```

## ./src/\_\_tests\_\_/game_tests.js

> This is the file where we will write our tests.

```bash
cat > ./src/__tests__/game_tests.js << EOF
const { faker } = require('@faker-js/faker'); // Vi använder faker för att skapa testdata.
const gameHandler = require('../domain/game.js');
const isUuid = require('uuid-validate');

/**
 * Test storage of games.
 */
describe('given a gameHandler', () => {
  describe('when creating game', () => {
    it('then should add one game', () => {
      const expectedNumberOfGames = gameHandler.getGames().length + 1;
      const game = gameHandler.createGame();
      expect(gameHandler.getGames().length).toBe(expectedNumberOfGames);
      expect(game.round).toBe(0);
      expect(isUuid(game.id, 4)).toBe(true);
    });
  });

  describe('when creating a game with name', () => {
    it('then should have correct name', () => {
      const expectedName = faker.name.lastName();
      const game = gameHandler.createGame(expectedName);
      expect(game.name).toBe(expectedName);
      expect(game.round).toBe(0);
    });
  });

});

/**
 * Test listing games!
 */
describe('given gameHandler', () => {
  describe('when listing games', () => {
    it('then should return array', () => {
      const game = gameHandler.createGame();
      const games = gameHandler.getGames();
      expect.arrayContaining(games);
    });
  });
});

/**
 * Test retrieving a game by id.
 */
describe('given gameHandler', () => {
  describe('when finding game', () => {
    const game = gameHandler.createGame();
    it('then should find game by id', () => {
      const foundGame = gameHandler.findGameById(game.id);
      expect(foundGame.id).toBe(game.id);
    });
  });
});

/**
 * Test adding a player to a game.
 */
describe('given gameHandler and a game', () => {
  let game = gameHandler.createGame();

  describe('when adding no players', () => {
    it('then should have game with no players', () => {
      expect(game.player1).toBe(null);
      expect(game.player2).toBe(null);
    });
  });

  describe('when adding player with no name', () => {
    it('then should have correct attributes', () => {
      game = gameHandler.addPlayer(game.id);
      expect(game.player1).not.toBe(null);
      expect(game.player1).toHaveProperty("id");
      expect(game.player1).toHaveProperty("name");
      expect(isUuid(game.player1.id, 4)).toBe(true);
      expect(game.player1.name).not.toBe(null);
    });
  });

  describe('when adding another player with no name', () => {
    it('then should have correct attributes', () => {
      game = gameHandler.addPlayer(game.id);
      expect(game.player2).not.toBe(null);
      expect(game.player2.name).not.toBe(null);
      expect(game.player1.id).not.toBe(game.player2.id);
    });
  });

});

/**
 * Testing to play game.
 */
describe.skip('given gameHandler with active game', () => {
  let game = gameHandler.createGame();

  describe('when adding player turn', () => {
    it('then should add stone to game', () => {
      game = gameHandler.play(game);
      expect(game.round).toBe(0);
    });
  });
});
EOF
```

## Test it

```bash
npm test
```
