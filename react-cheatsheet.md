<h1>Setup</h1>

<h3>...with create-react-app</h3>
<pre>sudo npm i create-react-app -g</pre>
Installs create-react-app globally.

<a href="https://github.com/facebook/create-react-app">more info</a>

<br>
<br>

<pre>create-react-app {foldername OR "." - for current folder}</pre>
or
<pre>npm init react-app {foldername OR "." - for current folder}</pre>
Installs a basic react app into the specified folder.

<h3>Loading Css Classes via imports (Css - Modules)</h3>

<pre>npm run eject</pre>
to get access to the configs folder!

</br>

Search for:
<code>test: cssRegex</code>
in the files:
<code>webpack.config.dev.json</code>
&
<code>webpack.config.prod.json</code>
 and add the following:
<pre>
modules: true,
localIdentName: '[name]__[local]__[hash:base64:5]'
</pre>

<h5>Result (webpack.config.dev.json):</h5>
<pre>
{
            test: cssRegex,
            exclude: cssModuleRegex,
            use: getStyleLoaders({
              importLoaders: 1,
              modules: true,
              localIdentName: '[name]__[local]__[hash:base64:5]'
            }),
          },
</pre>
<h5>Result (webpack.config.prod.json):</h5>
<pre>
{
            test: cssRegex,
            exclude: cssModuleRegex,
            loader: getStyleLoaders({
              importLoaders: 1,
              modules: true,
              localIdentName: '[name]__[local]__[hash:base64:5]',
              sourceMap: shouldUseSourceMap,
            }),
            // Don't consider CSS imports dead code even if the
            // containing package claims to have no side effects.
            // Remove this when webpack adds a warning or an error for this.
            // See https://github.com/webpack/webpack/issues/6571
            sideEffects: true,
          },
</pre>

<h3>Adding prop-types to a react project for type-validation</h3>

Installation:
<pre>npm install --save-dev prop-types</pre>

Import:
<pre>import PropTypes from 'prop-types';</pre>

restart server! <a href="https://reactjs.org/docs/typechecking-with-proptypes.html">More information</a>

<br>
<br>

<h3>adding Typescript</h3>

<pre>npm install --save typescript @types/node @types/react @types/react-dom @types/jest</pre>
<ul>
 <li> Rename any file to .tsx (i.e. App.js -> App.tsx)</li>
 <li> Also restart your server!</li>
 <li>Issues using Lib-Component (i.e. react-admin)? Add to tsconfig.json <pre>"noImplicitAny": false</pre> (find solution!)</li>
</ul>

<a href="https://facebook.github.io/create-react-app/docs/adding-typescript">More information</a>
