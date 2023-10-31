# edu-gomoku-local

> We test requirements from activity diagram.
>
> The tests can be run with **npm test**, or **npm run test:watch**

## Instructions 

```bash
cd ~
cd ws
cd gomoku-lab
touch ./src/__tests__/activity_diagram_tests.js
```

## ./src/gomoku.js

> This is minimum level for tests on previous level to go trough.

```bash
cat > ./src/game.js << EOF
const play = () => {}
const addPlayer = () => {}
const createGame = () => {}

module.exports = {play, addPlayer, createGame}
EOF
```

## ./src/\_\_tests\_\_/activity_diagram_tests.js

> These are the state transitions that we found in the state diagram.
> In the end these will become services, but for now we implement them in gomoku.js.

```bash
cat > ./src/__tests__/activity_diagram_tests.js << EOF
const gomokuHandler = require('../gomoku');
const gameHandler = require('../game');

describe('given a gomokuHandler', () => {
    describe('when created', () => {
      it('then should have expected properties', () => {
        expect(gomokuHandler).toHaveProperty('play');
        expect(gomokuHandler).toHaveProperty('isWin');
        expect(gomokuHandler).toHaveProperty('isTie');
        expect(gomokuHandler).toHaveProperty('createBoard');
      });
    });
});

describe('given a gameHandler', () => {
    describe('when created', () => {
      it('then should have expected properties', () => {
        expect(gameHandler).toHaveProperty('listGames');
        expect(gameHandler).toHaveProperty('findGameById');
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
