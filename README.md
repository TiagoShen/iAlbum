# iAlbum
An online album using angularJS, Nodejs, MongoDB and Express (MEAN)
Unzip iAlbum.rar
You need a few step to setup a server and database.
To setup database, you need to first download the lastest version of MongoDB from https://www.mongodb.org/.

I have already created an directory under iAlbum/data as a database for this app, if you want to 
setup another one, you need to do the following steps:

Create a directory under a certain path, I will represent this directory as: YourPath/iAlbum/data

Open the terminal, and setup an directory as your database by entering the following command:
./bin/mongod --dbpath [YourPath/iAlbum/data]

After starting the database server successfully, you should see some prompt in the terminal
like “I NETWORK [initandlisten] waiting for connections on port 27017”. This means that the
database server is up running now and listening on the default port 27017. Then leave this
terminal open and do not close it during your entire test, in order to allow
connections to the database from your Express app.

Open another terminal, switch to the directory where you installed your MongoDB and execute:
./bin/mongo

To run the MongoDB. Type the as below to switch to the database of yours.
use [iAlbum]

Since this app is focusing on the client side, I use database command to add users.
For example: 
db.userList.insert({'username': 'Eddie', 'password': '123456', 'friends':['Ken', 'Alice', 'Bill']})

The following line just show you how to upload a photo by typing command:
db.photoList.insert({'url': 'uploads/1.jpg', 'userid': 'xxxxxxx', 'likedby':['Ken', 'Alice']})

The 'userid' attribute is the primary key of userList records. Execute this to find the userid:
db.userList.find()

This way of uploading is just for debugging.
However, you can always upload your own photo using a browser once you logged in.

After you run the insert command, you should see “WriteResult({ "nInserted" : 1 })” on the
terminal. You can insert more records into the database collection to facilitate testing of
this program.

Now switch to the “iAlbum” project folder.
Then install the dependencies using the terminal as follows:
npm install

After this, we add 2 more Node.js packages to “iAlbum” project, which are mongodb and monk.
These 2 packages are used to interact with the MongoDB.

Now the final step. In the terminal, type “npm start” to start the Express app (you should always use control+C to kill an
already running app before you start the app again after making modifications). Check out
the rendered page again at http://localhost:3000/index.html on your browser.

You can add new photos to your album. Browse your friends' photos and hit "Like" if any of them impresses you.
