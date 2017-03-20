# JavaScript O-Standard Style

Airbnb JavaScript coding style + react + `.tsx` support.

Based on [Flet/semistandard](https://github.com/Flet/semistandard)

## Usage

The easiest way to use JavaScript Semi-Standard Style to check your code is to install it
globally as a Node command line program. To do so, simply run the following command in
your terminal (flag `-g` installs `semistandard` globally on your system, omit it if you want
to install in the current working directory):

```bash
npm install ostandard -g
```

After you've done that you should be able to use the `ostandard` program. The simplest use
case would be checking the style of all JavaScript files in the current working directory:

```
$ ostandard
Error: Use JavaScript Semi-Standard Style
  lib/torrent.js:950:11: Expected '===' and instead saw '=='.
```

### Custom Parser
To use a custom parser, install it from npm (example: `npm install
babel-eslint`) and add this to your package.json:

```json
{
  "ostandard": {
    "parser": "babel-eslint"
  }
}
```

### [Vim](http://www.vim.org/)

Install **[Syntastic][vim-1]** and add these lines to `.vimrc`:

```vim
let g:syntastic_javascript_checkers=['standard']
let g:syntastic_javascript_standard_exec = 'ostandard'
```

For automatic formatting on save, add these two lines to `.vimrc`:

```vim
autocmd bufwritepost *.js silent !ostandard % --fix
set autoread
```

[vim-1]: https://github.com/scrooloose/syntastic

### Ignoring files

Just like in `standard`, The paths `node_modules/**`, `*.min.js`, `bundle.js`, `coverage/**`, hidden files/folders
(beginning with `.`), and all patterns in a project's root `.gitignore` file are
automatically excluded when looking for `.js` files to check.

Sometimes you need to ignore additional folders or specific minfied files. To do that, add
a `semistandard.ignore` property to `package.json`:

```json
"ostandard": {
  "ignore": [
    "**/out/",
    "/lib/select2/",
    "/lib/ckeditor/",
    "tmp.js"
  ]
}
```

### Make it look `snazzy`
If you want prettier output, just install the [`snazzy`](https://github.com/feross/snazzy) package and pipe `semistandard` to it:

```bash
$ ostandard --verbose | snazzy
```

See [airbnb/javascript] for more information.

[airbnb/javascript]: https://github.com/airbnb/javascript
