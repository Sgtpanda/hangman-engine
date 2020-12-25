# hangman-engine
An edit of https://github.com/tameraydin/hangman-engine to support unicode characters like emoji

Hangman game engine

## Usage

```bash
npm install git+https://github.com/Sgtpanda/hangman-engine.git
```

```javascript
var hangman = require('hangman-engine.js')
// or window.hangmanEngine
var game = hangman.newGame('guess me');

game
  .start()
  .guess('g')
  .guess('u')
  .guess('e')
  .guess('s')
  .guess('m');
  .status; // 'WON'
```

## API

### Engine
HangmanEngine has 3 main methods:
- #### configure( *config* ):
  Pre-defines settings for the games that are going to be created.
  Defaults as following:
  ```javascript
  {
      maxAttempt: 10,
      concealCharacter: '*'
  }
  ```

  *Arguments*
  - ***config*** (Object): Configuration object to override defaults.

- #### reset():
  Resets configuration to the default.

- #### newGame( *phrase* ):
  *Arguments*: 
  - ***phrase*** (String): Phrase to guess.

  *Returns*: 
  - A HangmanGame object.

### Game
HangmanGame has 5 main methods:

- #### on( *event*, *callback* ):
  Binds callbacks for listeners.

  *Arguments*: 
  - ***event*** (String): Possible events are `'start'`, `'guess'` and `'end'`.
  - ***callback*** (Function): Callback will have the context of HangmanGame. Callback of `'guess'` event will have following arguments: *character*: guessed character, *isHit*: was the guess right, *isHint*: was guessed via **hint** method.

  *Returns*: 
  - (Object) Current game.

- #### start( *[force]* ):
  Starts the game.

  *Arguments*: 
  - ***force*** (Optional, String): Restarts the game; previously made guesses will be cleared.

  *Returns*: 
  - (Object) Current game.
  
- #### guess( *character* ):
  Guesses a character.

  *Arguments*: 
  - ***character*** (String): Character to guess.

  *Returns*: 
  - (Object) Current game.

- #### hint():
  Reveals first available character of the phrase.

  *Returns*: 
  - (Object) Current game.

- #### end( *[status]* ):
  Ends a started game with status `'QUIT'`.

  *Arguments*: 
  - ***status*** (Optional, String): Ends a started game with given status. Possible statuses are `'QUIT'`, `'WON'` and `'LOST'`.

  *Returns*: 
  - (Object) Current game.

- #### getConcealedPhrase():
  Provides the initial phrase as concealed with `concealCharacter`. Given the phrase to be 'a word' and 'r' character is guessed, then the result will be '&#42; &#42;&#42;r&#42;'.

  *Returns*: 
  - (String) Concealed phrase.

See /test for more info.

## License

MIT [http://tameraydin.mit-license.org/](http://tameraydin.mit-license.org/)
