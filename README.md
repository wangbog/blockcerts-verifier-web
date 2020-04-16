# @wangbog/blockcerts-verifier-web

A node.js web(express) for blockcerts verifier based on @wangbog/blockcerts-verifier.

**Note:** @wangbog/blockcerts-verifier (or the Blockcerts official source @blockcerts/blockcerts-verifier) is actually a browser-side component(javascript), the verification process is actually performed from client browsers, which means the blockchain APIs are requested directly from client browsers. The key thing that blockcerts-verifier dose is to define a <blockcerts-verifier> tag, so in this web project we can use it directly in our html code.

# Production
Clone this project from git:

```
  git clone https://github.com/wangbog/blockcerts-verifier-web.git
```

Use npm to install dependencies:

```
  cd blockcerts-verifier-web
  npm install
```

**Note:** @blockcerts/blockcerts-verifier suggest your html code import the blockcerts-verifier js lib this way: 

```
  <script src="node_modules/@webcomponents/webcomponentsjs/webcomponents-loader.js"></script>
  <script src="node_modules/@blockcerts/blockcerts-verifier/dist/main.js"></script>
```

This is a bad idea since /node_modules is a server side lib folder, we don't want the clients(browsers) know our directory path.
 
Instead, in app.js we have already make /blockcerts-verifier and /webcomponentsjs static routes to point to the real js lib in /node_modules, see app.js:

```
  app.use('/blockcerts-verifier', express.static(__dirname + '/node_modules/@wangbog/blockcerts-verifier/dist/'));
  app.use('/webcomponentsjs', express.static(__dirname + '/node_modules/@webcomponents/webcomponentsjs/'));
```

With this approach, in your html code you can just assign the src to these public paths, like:

```
  <script src="/webcomponentsjs/webcomponents-loader.js"></script>
  <script src="/blockcerts-verifier/main.js"></script>
```

Start express:

```
  npm start
```

Visit: http://localhost:3000 and verify your certificate.
