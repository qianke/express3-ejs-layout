

# express-ejs-layouts

#### *Layout support for ejs in express.*

[![build status](https://secure.travis-ci.org/Soarez/express-ejs-layouts.png)](http://travis-ci.org/Soarez/express-ejs-layouts)

## Installation
    npm install express-ejs-layouts

## Usage
    var express = require('express')
      , app = express()
      , expressLayouts = require('express-ejs-layouts')
    
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

With a layout

    <html>
    <body>
	<%- style %>
    <%- body %>
    <%- script %>
    </body>
	</html>

Renders

	<link src='render.css' />
    <script src='render.js'><script>
	<div>
		somethingsomething
    </div>

use:

    req.render('view')
	
result:
    <html>
    <body>
	<link src='render.css' />
    <div>
		somethingsomething
    </div>  
    </body>
	<script src='render.js'><script>
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