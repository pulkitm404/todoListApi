##Build a ToDo List Node.js RESTful API

#Tools (With Appropriate Links):
* [Node.js](https://nodejs.org/en/)
* [MongoDB](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/)
* Text Editor (_I used VS Code_)
* [Postman](https://www.postman.com/downloads/)

#Getting Started:

Make sure your environment is already set up, .i.e. Node.js and MongoDB is installed.

Running ``` npm -v ``` and ``` mongo --version ``` on the terminal/bash would verify that.

_If you don't have it installed, I've provided the links along with the tools._

>A basic knowledge about Nodejs and Mongo would suffice for you to create your first API.

#Additional Tools:

* We'll use express to set up a server, install it using ``` npm install express --save ```
* Secondly, we'll use nodemon to keep track of the changes and restarting the server automatically. Install it using ``` npm install --save-dev nodemon ```

#To Understand and Run the API:

* Clone the repo.
* Notice he Self Explanatory schema/model using Mongoose in api -> models
* The Routes being setup for our API calls in api -> routes, do you see some _predefined functions_ over there? Calm down. Next Point.
* The Controller ( api -> controllers ) defines all the functions used in the Routes. These functions use some basic Mongoose queries such as _find_ , _findById_ etc.
* Finally I've combined these elements in the server.js file with a little bit of parsing, registering and encoding which basically :
    * Connects your database by adding a url to the mongoose instance connection.
    * Loads the created model.
    * Installs bodyParser and use it to parse the body for the middlewares otherwise middlewares return an empty object.
    * Register our created routes in the server
* Start the MongoDB server using ``` mogod ```
* Refresh the node server by running ``` rs ```

#Testing via Postman:

* Open up Postman and type : ``` http://localhost:3000/tasks ``` in the url bar and press enter.
> This would return a [] because the databse is empty :) Let's stack up the databse.

* On the same url, change the method to POST -> Click on body -> select "x-www-form-urlencoded" -> enter "name" as the key and "Demo Task" as the value and click send.

    * This should give you a response Status : 200 OK, which would look something like this :
    ![Demo](/demo.png)


Having done all these, what happens if we entered a wrong route? 

Adding this snippet to your server.js file would handle that:
``` 
app.use(function(req, res) {
  res.status(404).send({url: req.originalUrl + ' not found'})
});
```
That's it folks! 
By @pulkitm404