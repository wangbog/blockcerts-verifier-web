# @wangbog/blockcerts-verifier-web

基于node.js的web展示项目(express)，用于验证并展示blockcerts证书，其引用了@wangbog/blockcerts-verifier项目。

**注：** @wangbog/blockcerts-verifier项目（以及对应的Blockcerts官方项目@blockcerts/blockcerts-verifier），本质上就是一个浏览器控件（javascript），验证的流程其实是由用户浏览器发起的，这意味着对应的区块链API的请求是有用户浏览器发起的查询。blockcerts-verifier提供的最核心的功能就是它定义了blockcerts-verifier这个HTML标签，所以在本web项目中，我们直接在HTML代码中使用这个标签即可。

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
