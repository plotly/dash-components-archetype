# Dash Components Archetype

## Overview

This is a [Builder][] archetype for [Dash][] component suites. It defines build-
and test configuration, as well as development scripts and a convenient way to
generate a new component suite project with all the necessary boilerplate.

## Generating a component suite project

```sh
$ npm install -g builder-init
$ builder-init dash-components-archetype
```

Answer the prompts, then:

```sh
$ cd [YOUR-COMPONENT-SUITE-NAME]
$ npm install
```

## Development

### Demo Server

If your component suite project has a `demo/` directory following the same
structure as the [`init/demo`](./init/demo) directory in this archetype, you can
start up a demo development server:

```sh
$ npm run demo
$ open http://localhost:9000
```

This lets you see a demo of the rendered components. You have to maintain the
list of components in `demo/Demo.react.js`.

### Code quality

To run lint:

```sh
$ npm test
```

TODO: ESLint is not reporting problems
https://github.com/plotly/dash-components-archetype/issues/15

### Testing your components in Dash

The best way to test your components in the real Dash context is by linking into
`dash2` and testing them from there.

1. Prepare your component suite module by linking and watching for changes

        # Symlink module
        $ npm link

        # Transpile components to `lib/` and watch for changes
        $ npm start

2. Link module into `dash2` project

        # In the `dash2/renderer` project directory:
        $ npm link [YOUR-COMPONENT-SUITE-NAME]

Now you should be able to restart the webpack process (in `dash2/renderer`:
`ctrl-c`, `npm start`), after which webpack will automatically pick up new
changes to the component suite.


## Customizing your project

You can override any `npm` script in the archetype with your own implementation.
To see the list of supported scripts, run `./node_modules/bin/builder run`. For
more details, see [Builder Archetypes][].

## Release

To tag and release a new version of the archetype, follow these instructions.
You might be tempted to add some of these steps to NPM's `*version` lifecycle
methods, but that would interfere with versioning and publishing of the actual
project depending on the archetype, since [Builder][] merges the project
package.json scripts with the archetype's package.json scripts.


```sh
# 1. Bump package.json `version` according to [semver][]
vi package.json

# 2. Generate `dev/*` package files
node_modules/.bin/builder-support gen-dev

# 3. Run tests
npm run builder:check

# 4. Commit and tag
git add package.json dev
git commit -m "vx.x.x"
git tag -a "vx.x.x" -m "vx.x.x"
git push --follow-tags

5. Publish main and dev package
npm publish && cd dev && npm publish && cd -
```

[Builder]: https://github.com/FormidableLabs/builder
[Builder Archetypes]: https://github.com/FormidableLabs/builder#archetypes
[Dash]: https://plot.ly/dash
[dash-core-components]: https://github.com/plotly/dash-core-components
[semver]: http://semver.org/

## Contributing

You can test component generation with this library with `npm link` and with the absolute file path option of `builder-init`.

```
npm install -g builder-init
git clone https://github.com/plotly/dash-components-archetype.git
cd dash-components-archetype
npm link
cd dash-components-archetype-dev
npm link
cd ../..
builder-init /ABSOLUTE/PATH/TO/dash-components-archetype/
# answer prompts to create new file

# Enter new package folder
cd new-package # replace with the name of your package from the prompt
npm link dash-components-archetype
npm link dash-components-archetype-dev
npm i
```
