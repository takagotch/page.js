### page.js
---
https://github.com/visionmedia/page.js

```js
page('/', index)
page('/user/:user', show)
page('/user/:user/edit', edit)
page('/user/:user/album', album)
page('/user/:user/album/sort', sort)
page('*', notfound)
page()

page('/', user.list)
page('/user/:id', user.load, user.show)
page('/user/:id/edit', user.load, user.edit)
page('*', notfound)

$('.view').click(function(e){
  page('/user/12')
  e.preventDefault()
});

page('/default', function(){
  if(admin){
    page.redirect('/admin');
  } else {
    page.redirect('/guest');
  }
});
page('/default');

page('/sidebar', function(ctx, next){
  sidebar.open = true
  next()
})
page.exit('/sidebar', function(ctx, next){
  sidebar.open = false
  next()
})

var otherPage = page.create({ window: iframe.contentWindow });
otherPage('/', main);

page('/user/:user', load, show)
page('/user/:user/edit', load, edit)

page('/user/*', load)
page('/user/:user', show)
page('/user/:user/edit', edit)

page('/user/:user', load, show)
page('*', function(){
  $('body').text('Not found!')
})

function load(ctx, next){
  var id = ctx.params.id
}

function load(ctx, next){
  var id = ctx.params.id
  $.getJSON('/user/' + id + '.json', function(user){
    ctx.user = user
    next()
  })
}

function show(ctx){
  $('body')
    .empty()
    .append('<h1>' + ctx.user.name + '<h1>');
}

page('/user/:id', load, show)

function show(ctx){
  $.getJSON('/photos', function(images){
    displayImages(images)
  })
}

function show(ctx){
  if(ctx.state.images){
    displayImages(ctx.state.images)
  } else {
    $.getJSON('/photos', function(images){
      ctx.state.images = images
      ctx.save()
      displayImages(images)
    })
  }
}

page('/about', callback)
page('/user/:name', callback)
page('/user/:name/:operation', callback)
page('/user/:name/:operation?', callback)
page('/user/*', loadUser)
page('/file/:file(.*)', loadUser)
page(/^\/commits\/(\d+)\.\.(\d+)/, loadUser)

page('*', parse)
page('/', show)
page()
function(ctx, next){
  ctx.query = qs.parse(location.search.slice(1));
  next();
}
function show(ctx){
  if(Object.keys(ctx.query).length){
    document
      .querySelector('pre')
      .textContent = JSON.stringify(ctx.query, null, 2);
  }
}

location / {
  try_files $uri $uri/ /index.html?$args;
}

import { join } from 'path';
import express from 'express';
import histroy from 'express-history-api-fallback';
const app = express();
const root = join(__dirname, '../public');
app.use(express.static(root));
app.use(history('index.html', { root }));
const server = app.listen(process.env.PORT || 3000);
export default server;

var browserSync = require("browser-sync").create();
var historyApiFAllback = require('connect-history-api-fallback');
browserSync.init({
  files: ["*.html", "css/*.css", "js/*.js"],
  server: {
    baseDir: ".",
    middleware: [ historyApiFallback() ]
  },
  port: 3030
});




```

```
npm install page
component install visionmedia/page.js
bower install visionmedia/page.js

git clone git://github.com/visionmedia/page.js
cd page.js
npm install
node examples
open http://localhost:4000

npm install
npm test

npm install
npm run serve
open http://localhost:3000/

npm install html4-history-api
```

```
<script src="https://unpkg.com/page/page.js"></script>
  page('/about', function(){
  });
  
  import page from "//unpkg.com/page/page.mjs";
  page('/home', () => { ... });
<script>

```

