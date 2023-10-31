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
const ERR_MSGS = require('../error_messages');
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
EOF
```

## Test it

> Try solving all requirements, soluting will be shown in next level.

```bash
npm test
```
