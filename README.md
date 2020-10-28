# First-node-project
# Steps for Node Project

### Make a new directory
### Type npm init, use nmp init -y to skip through the extra questions it asks
### Create files in the directory of files you want to run
### To test what you have, console log your message then in the terminal type node then the file you want to want to check. ex: node index.js


# More Instructions

### To make an express app you need to import the express module into index.js, create an instance, and just require.
### To add a gitignore you need to add a file in the project your in named .gitignore.
### Home hello world route: 
### app.get('/', (req, res)=>{
### res.send('Hello world!')
### res.sendFile()
### res.render
### })


# ………………. Creating a Home Route: …………………….

### Remember, this goes before the app.listen in your index.js file.

### app.get(‘/‘, (req, res) =>{ res.send(“hello world”) })

### Now go to your browser, type localhost:8000 You should see hello world.

# ……………………….GIT IGNORE ……………………..

### To ignore files: Create a .gitignore file inside the folder Inside the .gitignore file, write the file name that you don’t want inside it. such as node_modules. Files you ignore, won’t be pushed.

# ……………………CREATING A NODE APP (EJS & EJS LAYOUT NOTES)……………

### Inside terminal write the following commands: npm i ejs =installs ejs npm i express-ejs-layouts

### THEN inside your index.Js file write: const ejsLayouts = require(‘express-ejs-layouts’) app.set(‘view engine’, ‘ejs’) app.use(ejsLayouts)

# ………………. CREATING A NODE APP (VIEWS Folder NOTES)…………..

### Now that you have installed ejs & ejs layouts Make a new folder called Views Inside views, make a file called layout.ejs
<!DOCTYPE html>

### <%- body %>
### REMEMBER TO PUT <%- body %> inside the body tag, so it links the ejs files.

### ** you need to use <% JAVASCRIPT %> around any javaScript code. **

### LETS SPICE THIS UP! Inside the views folder, create another file. Name it, index.ejs
### Now, go back to the entry file, which is index.js and re-write the home route.

### app.get('/', (req, res)=>{
###    res.render('index')
### })
### res.render responds with ann ejs file, in this case we are responding with the index.ejs file.

### Inside the index.ejs write: <h1> This is my Home Route! </h1>

### Once the user visits the local host, they should see “This is my home Route!”

# ……………………CONTROLLER NOTES……………………….

### It is very easy to get overwhelmed with multiple ejs files, therefore, controllers is a great way to organize. Create a controllers folder, inside the folder, create a .js file. Inside that file, you can write your routes. For example, on our RESTful created assigment, we had 1 controllers folder with 2 files inside. Once file for Dinosaurs.js and the other Creatures.js all the routes associated with dinosaurs were kept inside the Dinosaurs.js file. All the routes associated with creatures were kept inside the Creatures.js file. Now, let’s use the example above. If we move it to the Dinosaurs.Js file, it would now look like this:

### router.get('/', (req, res)=>{
###     res.render('index')
### })
### Because this is inside the Dinosaurs.js file, the browser reads it as LocalHost:8000/dinosaurs. It will still respond with the index.ejs file.

# ……………………..SQL COMMANDS………………

### What is SQL? SQL stands for Structured Query Language. SQL is used to communicate with a database.Great for updating data on a database, or retrieve data from a database

### Psql into terminal access the sql terminal

### q = goes back to terminal screen

### \l = lets you view all the databases(lower L)

### \c database name = connects to the database

### \d table name = look at the structure of the table

### \dt = views the tables in the database you’re connected to.

# …………………..To create & Use a Database Using Sql: …………….

# CREATE DATABASE grocery;

### To create a Table inside database: CREATE TABLE produce (id SERIAL PRIMARY KEY, name TEXT, price VARCHAR(5), color TEXT);

### To see all the required fields of a table: SELECT * FROM produce;

### Adding to table: INSERT INTO produce (name, price, color) VALUES (‘potato’, 3, ‘brown’);

### How to delete a table or database: DROP TABLE produce; DROP DATABASE grocery;

### How to find a field in a table: SELECT * FROM example WHERE name = ‘Paul’;

### How to change/update 1 field in table: UPDATE produce SET color=’orange’ WHERE name = ‘potato’;

### How to find how many values in a column: SELECT COUNT(price) FROM produce;

### How to group by: SELECT price FROM produce GROUP BY price;

### How to Temporarily change a column name: SELECT name, price AS itemPrice FROM produce;

### How to delete a column from a table: ALTER TABLE produce DROP price;

### How to find the highest value of a column: SELECT name, price FROM produce
WHERE price = ( SELECT MAX(price) FROM produce);

# ……………………SQL % TIPS:……………………

### SELECT * FROM produce WHERE name LIKE ‘%eese’; == this will show me any produces that end with eese SELECT * FROM produce WHERE name LIKE ‘che%’; == this will show me any produces that start with che

# ……………………..SEQUELIZE NOTES ………………….

### WHAT IS ORM? Literally means Object Relational Mapper. But basically this means we can use JavaScript to create and work with SQL. Instead of having to go out of JavaScript to access databases.

### Go on iTerm and go to your SEIFX818 folder (or folder of your choice) 1st Command: npm i -g sequelize-cli (if you get an error try: sudo npm i -g sequelize-cli)

### Then make a new folder: mkdir userapp

### Cd into that new folder, we are making a node app so: 2nd command: npm init -y 3rd command: touch index.js .gitignore 4th command: npm i pg sequelize (always needs to be installed to use sequelize) Now you can do: code .

### Now inside VS Code:

### Go inside your .gitignore file write: node_modules .env

### Go inside your terminal in VS code: 1st command inside VS code: sequelize init This command will create a config folder (w/ a config.json file) , migrations folder & models folder(will have an index.js inside.. don’t use it).

# Preparing for Database:

### Inside the Config Folder, there is a config.json file. Inside that file remove the following: delete the “username” & “password” fields (3 of them) change the “dialect’: “mysql” to dialect’: “postgres” (3 times) on the database fields change the word in front of _development. _test _production to the name of your app an example of this would be if my app is called userapp. It would say: “database”: “userapp_development”

# Creating the Database:

### Go back on the VS terminal and create a new database. 2nd command inside VS code: sequelize db:create userapp_development
### Check if it was created by doing psql and then \l if it was created, you should see the database in the list. Then do \q

# Creating a table inside the database:

### 3rd command inside VS code:  
###  sequelize model:create —name user —attributes firstName:string,lastName:string,age:integer,email:integer
###   Breakdown of that command: create a new table/model called user.
###  The attributes aka columns are first name, last name, age & email.
### Check to see if this table was created by go to your models folder, there should be an user.js file. It should have some code in it. 4th command inside Vs code: sequelize db:migrate to undo the migration: sequelize db:migrate:undo This creates a migration from our javascript file to our sql database. To check this, do: psql
### \l.
### \c userapp_development.
### \dt to see the user table we just created.

### Lets use our table using javascript:

### Inside index.js do: const db = require (‘./models’)

### For further notes.

## https://tmdarneille.gitbook.io/seirfx/05-node-express/04usingmodels

# Instructions on migration stuff

### First install npm install -g sequelize-cli right on the terminal
### Then make your files and npm init -y (ex: mkdir userapp, cd userapp, npm init -y, touch index.js, echo "node_modules" >> .gitignore)
### Install sequelize; npm install pg sequelize
### Make a table with seqelize; sequelize db:create userapp_development
