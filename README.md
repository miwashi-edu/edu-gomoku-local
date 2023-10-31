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
touch ./src/__tests__/state_diagram_tests.js
```

## ./src/\_\_tests\_\_/state_diagram_tests.js

> These are the state transitions that we found in the state diagram.
> In the end these will become services, but for now we implement them in gomoku.js.

```bash
cat > ./src/__tests__/state_diagram_tests.js << EOF
const gomokuHandler = require('../game');
const ERR_MSGS = require('../error_messages');

describe('given gameHandler', () => {
  describe('when using ', () => {
    it('should have expected properties', () => {
      expect(gameHandler).toHaveProperty('play');
      expect(gameHandler).toHaveProperty('addPlayer');
      expect(gameHandler).toHaveProperty('createGame');
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
