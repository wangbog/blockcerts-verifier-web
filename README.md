# @wangbog/blockcerts-verifier-web
A node.js web(express) for blockcerts verifier based on @wangbog/blockcerts-verifier

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

This is a bad idea since node_modules is a server side lib folder, we don't want the clients(browsers) know our directory path.
 
Instead, in app.js we have already make /blockcerts-verifier and /webcomponentsjs static routes to point to the real js lib in /node_modules, see app.js:

```
  app.use('/blockcerts-verifier', express.static(__dirname + '/node_modules/@wangbog/blockcerts-verifier/dist/'));
  app.use('/webcomponentsjs', express.static(__dirname + '/node_modules/@webcomponents/webcomponentsjs/'));
```

With this approach, in your html you can just assign the src to these public paths, like:

```
  <script src="/webcomponentsjs/webcomponents-loader.js"></script>
  <script src="/blockcerts-verifier/main.js"></script>
```

Start express:

```
  npm start
```

Visit: http://localhost:3000 and verify your certificate.
