# Chessground

[![Continuous Integration](https://github.com/ornicar/chessground/workflows/Continuous%20Integration/badge.svg)](https://github.com/ornicar/chessground/actions?query=workflow%3A%22Continuous+Integration%22)
[![npm](https://img.shields.io/npm/v/chessground)](https://www.npmjs.com/package/chessground)

![Chessground in 2D and 3D](/screenshot/twin.jpg)

_Chessground_ is a free/libre open source chess UI developed for
[lichess.org](https://lichess.org).
It targets modern browsers, as well as mobile development using Cordova.

## License

Chessground is distributed under the **GPL-3.0 license** (or any later version,
at your option).
When you use Chessground for your website, your combined work may be
distributed only under the GPL. **You must release your source code** to the
users of your website.

Please read more about GPL for JavaScript on [greendrake.info/#nfy0](http://greendrake.info/#nfy0).

## Demos

- [Chess TV](https://lichess.org/tv)
- [Board editor](https://lichess.org/editor)
- [Puzzles](https://lichess.org/training)
- [Analysis board](https://lichess.org/ofWXRFGy)
- [Game preview](https://lichess.org/games)

## Features

Chessground is designed to fulfill all lichess.org web and mobile apps needs, so it is pretty featureful.

- Well typed with TypeScript
- Fast. Uses a custom DOM diff algorithm to reduce DOM writes to the absolute minimum.
- Small footprint: 10K gzipped (31K unzipped). No dependencies.
- SVG drawing of circles, arrows, and custom user shapes on the board
- Arrows snap to valid moves. Freehand arrows can be drawn by dragging the mouse off the board and back while drawing an arrow.
- Entirely configurable and reconfigurable at any time
- Styling with CSS only: board and pieces can be changed by simply switching a class
- Fluid layout: board can be resized at any time
- Support for 3D pieces and boards
- Full mobile support (touchstart, touchmove, touchend)
- Move pieces by click
- Move pieces by drag & drop
  - Minimum distance before drag
  - Centralisation of the piece under the cursor
  - Piece ghost element
  - Drop off revert or trash
- Premove by click or drag
- Drag new pieces onto the board (editor, Crazyhouse)
- Animation of pieces: moving and fading away
- Display last move, check, move destinations, and premove destinations (hover effects possible)
- Import and export positions in FEN notation
- User callbacks
- No chess logic inside: can be used for [chess variants](https://lichess.org/variant)

## Installation

```sh
pnpm install --save chessground
```

### Usage

```js
const Chessground = require('chessground').Chessground;

const config = {};
const ground = Chessground(document.body, config);
```

### Wrappers

- React: [ruilisi/react-chessground](https://github.com/ruilisi/react-chessground)
- Vue.js: [vitogit/vue-chessboard](https://github.com/vitogit/vue-chessboard)
- Angular: [topce/ngx-chessground](https://github.com/topce/ngx-chessground)

More? Please make a pull request to include it here.

## Documentation

- [Config types](https://github.com/ornicar/chessground/tree/master/src/config.ts)
- [Default config values](https://github.com/ornicar/chessground/tree/master/src/state.ts)
- [API type signatures](https://github.com/ornicar/chessground/tree/master/src/api.ts)
- [Examples repo](https://github.com/ornicar/chessground-examples/tree/master/src/units)
- [Base CSS](https://github.com/ornicar/chessground-examples/blob/master/assets/chessground.css)

## Development

Commands are listed in package.json.
In case you want to see the possibilities from the console, run `pnpm run`

### Install build dependencies:s

```sh
pnpm install
```

### Update deps:

```sh
rm -rf node_modules pnpm-lock.yaml && pnpm store prune && pnpm install
```

### Build the node module:

```sh
pnpm prepare --watch
```

### Build the minified bundled dist files: (NOTE: from lila you will likely then need to restart the build as it does not watch for changes on the minified file):

```sh
pnpm dist
```

### Run tests:

```sh
pnpm run test --watch
pnpm run test fen --watch
```

### Before committing:

```sh
pnpm run lint
pnpm run format
```

### Watch chessground changes from another project:

In other project:

- declare the link towards chessground (from project's `package.json`)

```json
  "dependencies": {
    ...
    "chessground": "link:/path/to/chessground",
    ...
  }
```

In chessground:

- create `.env.local` file based on .env.local.default
- link back:

```sh
    pnpm run link
```

- trigger compilation and generate minified file:

```sh
  pnpm run local-dist
```
