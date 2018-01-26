# meanauthapp

1)to code this meanauthapp, we first init the app and declare the starting point of the app as app.js.

2)we first of all import all the frames and Middleware required to the file. eg bodyParser(to take the data from the frontend form),  CORS(this acts as a connection/Middleware between the frontend and the backend. this is required since db is at different port, frontend at different port and the backend at the different port).

3)we make the connection to the db and give the output of the success or the failure. We also declare the port no.

4) using the app const to call express and make the main directory using ```
app.use(express.static(path.join(__dirname, 'public')));
```
the bodyParser using ```app.use(bodyParser.json());
```
and the main home page route as ```
app.get('/', (req, res) => {
  res.send('Invalid Endpoint');
});
```
We also use the listen function from the app and log the message on success.

5)Then, we make a directory called routes and file named ```users.js``` in it.
This file contains all the routes/the urls which will redirect the page.


6)Once again, we import all the important packages we need i.e. express, passport, jsonwebtoken(this provides the token on successful authentication).
We use the Router function of the express module to route the urls.
Also, we import the models(db) because when the ```register```, all the data goes to the db.

7)we export the module because it will be needed in other files too.
``` const User = module.exports = mongoose.model('User', UserSchema);
```
In this line, we create a variable named `User` and export it so that we can use it from outside. ```mongoose.model('variable name', db schema variable)```

8)Now, we create a directory `models` with file named `users.js`. This file would contain the schema(design/layout) of our database, and all would respond to all the queries by interacting with the db.

9) we use bcryptjs to hash the password and call the db from `config/database.js`

10) We want to create 2 function, one to get the user by their id and the second by their username.
Since these are the two functions which we will need from outside the file hence we will export them using ``` module.exports.getUserById ```
