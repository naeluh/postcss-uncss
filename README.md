# postcss-uncss

Use [giakki/uncss](https://github.com/giakki/uncss) as a [PostCSS](https://github.com/postcss/postcss) plugin.

## About

UnCSS is a tool that removes unused CSS from your stylesheets. It works across multiple files and supports Javascript-injected CSS.

### How?

The HTML files are loaded by [PhantomJS](https://github.com/Obvious/phantomjs) and JavaScript is executed. UnCSS filters out selectors that are not found in the HTML files.

See the [UnCSS](https://github.com/giakki/uncss) docs for more information.

## Installation

```bash
npm install postcss-uncss
```

## Usage

```js
postcss([ require('postcss-uncss') ])
```

See [PostCSS](https://github.com/postcss/postcss) docs for examples for your environment.

## Options

- **html** (Array): provide a list of html files to parse for selectors and elements. Usage of [globs](https://github.com/isaacs/node-glob) is allowed.

- **ignore** (Array): provide a list of selectors that should not be removed by UnCSS. For example, styles added by user interaction with the page (hover, click), since those are not detectable by UnCSS yet. Both literal names and regex patterns are recognized. Otherwise, you can add a comment before specific selectors in your css:

  ```css
  /* uncss:ignore */
  .selector1 {
      /* this rule will be ignored */
  }

  .selector2 {
      /* this will NOT be ignored */
  }
  ```

### Example Configuration

```js
{
  html: ['index.html', 'about.html', 'team/*.html'],
  ignore: ['.fade']
}
```