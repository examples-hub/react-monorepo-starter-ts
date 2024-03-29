# react-monorepo-starter-ts

- quickstart monorepo example for react projects and vanillajs projects

# overview

- tech-stack
  - react 17
  - typescript 4
  - monorepo
    - A mix of TypeScript and Javascript packages
    - npm workspaces only, no lerna
    - yarn workspace should work too, but not tested here
  - webpack 5
    - webpack config shared at top level with webpack-merge
    - hot reloading with react-refresh-webpack-plugin
  - babel
    - react components lib is compiled with babel
    - react app is compiled with webpack and babel-loader
  - jest for testing
  - styling
    - support scss, css
  - other dev tools
    - eslint
    - prettier

- project-structure
  - package-a: simple utils
  - packages
    - sample-app: simple react app
    - sample-components: simple react components

- all dependencies are hoisted to top-level `node_modules` using npm workspaces(require npm 7+)
  - put all your deps of dev/build/test/engineering at top level

# usage

- requirements
  - npm 7+

``` bash
# npm install --legacy-peer-deps
npm i
npm start
```

- open a browser and go to http://localhost:8999

# notes and issues

- npm 7 workspaces limitations
  - no equivalent of `yarn workspaces run cmd`
  - no equivalent of `yarn workspace workspaceName cmd`

- The `main` field of all `package.json`s points to `src` for easier development
  - `import`s in jest testing use `main`
  - `import`s in vscode ide use `main` for code jumping
  - `import`s in webpack use `module`
- If you want to publish a package, it's better to point `main` to `dist` in the package.json

- `APP_ENV` environment variable
  - if no value is set, building es6 and ts is supported, but not react
  - if `react*` is set, building react is supported
  - if `reacthot` is set, react hot reloading is supported
  - see `babel.config.js` file for details and package.json scripts for examples

# roadmap

- new demo page

- css url
  - image url

- storybook(too many breaking changes recently, not planned until stable)
  - support component story format
  - support mdx docs

# license

[MIT](https://opensource.org/licenses/MIT)
