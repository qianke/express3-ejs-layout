

# express3-ejs-layout

#### *Layout support for ejs in express.*

[![build status](https://secure.travis-ci.org/Soarez/express-ejs-layouts.png)](http://travis-ci.org/Soarez/express-ejs-layouts)

## Installation
    npm install express3-ejs-layout

## Usage
    var express = require('express')
      , app = express()
      , expressLayouts = require('express3-ejs-layout')
    
    app.set('view engine', 'ejs')
    app.set('layout', 'myLayout') // defaults to 'layout'     

    app.use(expressLayouts)
    app.use(app.router)
    
    app.get('/', function(req, res){
      res.render('aView', { layout: 'someSpecificLayout' })
    })

    app.listen(3000)

### styles and scripts
If you like to place scripts in your view, you can do it like this:

layout.html

    <html>
	<title><%= title %><title>
	<link src='main.css' />
	<%- style %>
    <body>	
    <%- body %>
	<script src='main.js'><script>
    <%- script %>
    </body>
	</html>

render.html

	<link src='render.css' />
    <script src='render.js'><script>
	<div>
		something
    </div>

render.js

    req.render('render',{title:'render'})
	
result:

    <html>
	<title>render</title>
	<link src='main.css' />	
	<link src='render.css' />
    <body>
    <div>
		something
    </div>
	<script src='main.js'><script>
	<script src='render.js'><script>
    </body>
	</html>
	
	
### contentFor

A view

    somebody
    <%- contentFor('foo') %>
    club
    <%- contentFor('bar') %>
    fight

With a layout

    <%-bar%> <%-foo%>
    <%-body%>

Renders

    fight club
    somebody

MIT