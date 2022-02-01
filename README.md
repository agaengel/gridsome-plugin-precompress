# gridsome-plugin-brotli
[![CI](https://github.com/agaengel/gridsome-plugin-precompress/workflows/CI/badge.svg)](https://github.com/agaengel/gridsome-plugin-precompress/actions)
[![Known Vulnerabilities](https://snyk.io/test/npm/gridsome-plugin-precompress/badge.svg)](https://snyk.io/test/npm/gridsome-plugin-precompress)
[![Coverage Status](https://coveralls.io/repos/github/agaengel/gridsome-plugin-precompress/badge.svg?branch=main)](https://coveralls.io/github/agaengel/gridsome-plugin-precompress?branch=main)

Gridsome plugin for preparing brotli and gzip pre compressed versions of assets.

> Based on [gatsby-plugin-brotli](https://github.com/ovhemert/gatsby-plugin-brotli) and [gridsome-plugin-brotli](https://github.com/thetre97/gridsome-plugin-brotli)

## Requirements

This plugin will only generate the compressed files. You need to configure your webserver to serve these precompressed files and not recompress them on the fly. The Gridsome development server **does not** serve the compressed versions.

## Installation

With npm:

```bash
yarn add gridsome-plugin-precompress # or
npm install gridsome-plugin-precompress
```

## Usage

`gridsome.config.js`
```javascript
module.exports = {
  plugins: ['gridsome-plugin-precompress']
}
```

# Options

By default, only `html`, `.css` and `.js` files are compressed, but you can override this with the `extensions` option.

```javascript
module.exports = {
  plugins: [
    {
      use: 'gridsome-plugin-precompress',
      options: {
        extensions: ['css', 'html', 'js', 'svg', 'json']
      }
    }
  ]
}
```

You can even place all the brotli-compressed files (only the brotli ones, the uncompressed ones will
be saved in the `dist` directory as usual) in a dedicated directory (ex. `dist/compressed`):

```javascript
module.exports = {
  plugins: [
    {
      use: 'gridsome-plugin-precompress',
      options: {
        path: 'compressed'
      }
    }
  ]
}
```

It's possible to deactivate brotli via brotli: false or gzip with gzip: false

The option wait define a sleep time before searching for the files to compress in the dist folder e.G. if you have other code also running at api.afterBuild that generates files in the dist folder that you also want to compress.  

## License

Licensed under [MIT](./LICENSE).

_NOTE: This plugin only generates output when run in `production` mode! To test, run: `gridsome build` and view the `dist` folder._
