When I wanted to upgrade from being a Front End Developer to a Full Stack Developer, I had trouble finding an article that encompassed the concepts of all the different skills I needed to learn in able to become one.

Knowledge of databases, familiarity with a back-end language and how to integrate the back-end with my front-end app were skills that I didn’t know yet. That is what pushed me to create this article: to solve that in order to help myself and for my fellow software engineers out there.

I’ve included the git repository link of the whole code at the end of the article but I suggest that you take this article step-by-step before checking the repo out. It will help you understand the tutorial better. :)
“What will we build”

Here is what our app will look like once we’ve finished building it.

The front end allows us to view the current information inside our database. It also allows us to add new data into it, delete a present data and update an already existing one.

We will build it from nothing. We will setup our own database, create the back end from the ground up and bootstrap our front end with the bare minimum.

So, get yourselves strapped in and get your coding fingers ready!
First Things First

Let’s create our project’s main directory. This will hold both the code for the front and back end of our app.

mkdir fullstack_app && cd fullstack_app

Then, let’s start off with our front end. We will use create-react-app to bootstrap our front end, which means that we will not have to worry about setting up Webpack or Babel (as create-react-app sorts this all out by default). If you don’t have create-react-app globally installed yet, fret not, installing it is easy, just type this into our project’s main directory command line.

npm i -g create-react-app

After this, we can now create our react app with create-react-app (pun intended). To do this, just type this in the command line.

create-react-app client && cd client

We will also need Axios in order to make get/post requests with ajax. So let’s install that now:

npm i -S axios

Wait for it to finish and then let’s proceed in organizing the front end so it will be easy to incorporate our back end later.

For PC users:

del src\App.css src\App.test.js src\index.css src\logo.svg\

For MAC users:

rm src/App.css src/App.test.js src/index.css src/logo.svg

Then, let’s edit our App.js file inside the client folder and let it just render something simple. We will further edit this file later on when we have our back end ready.
“React app ready”

We also have to edit our index.js and remove one line of code from there. We just have to remove the import ‘./index.css’; part of the code and we can now start our react app.
“index.js”

In order to start our front end, just type this in the command line.

npm start

and go to your browser and type http://localhost:3000/. You can now see that our front end is up and running.
Back It Up Just a Tad

Time to set-up our back end. Go back to our main directory and let’s create our back end directory from there. We will also initialize this directory so that we’ll have our package.json ready for building. Your terminal will prompt you to enter some details for the package.json, just keep pressing enter until it is done.

mkdir backend && cd backend
npm init

Create a new file that will serve as our main code for the back end and name it server.js. Then, type the following into it. This back end code is pretty blunt and basic, I have only created it so that beginners won’t have to think much of the complexity of the code rather than they would think about the code’s intent. Then, they could easy manipulate it afterwards once they wrapped their heads around it. I’ve put comments beside every method for ease of understanding.
“Spine of every web app”

You might have noticed that a database link is already used in our back end code. Don’t worry, that’s the next step in our article. Setting it up will also be as easy as the past few steps. First, head on to MongoDB atlas and create an account there. MongoDB Atlas will let us use a free 500 MB of MongoDB database and use it remotely. It is also hosted in the cloud. This is the current trend of our industry and acquiring skills that enables us to use cloud database is a real asset nowadays.

After setting up your account, log into your account. Follow the steps prompted by the website in creating your own cluster and cluster/database users. Here is the checklist or steps in order to create your own mongoDB database.

    Build your first cluster.
    Create your first database user.
    Whitelist your IP address (in our case, the localhost:3001)
    Connect your cluster.

We need to get the connection string of our database, so for step 4 we just need to click the connect button of our created cluster as shown below.
cluster connection

Then click “choose a connection method” at the bottom part of the modal, select “Connect your Application”. Then, copy the string show by the modal.
connection string

Paste this string uri in your server.js file. Find the dbRoute variable and put the link with your credentials there as a string.

Now, back to our back end source code. We will now configure our database, in order to do so, create a file named data.js. It should have the following code inside it.
“MongoDB, Baby”

We are almost DONE! Let’s just install our back end’s package and modules and we are good to go. Just pass this line on your command line.

npm i -S mongoose express body-parser morgan cors

Now, if we launch our back end using

node server.js

We can see in our console that it is ready and is listening on port 3001. Let’s go back to our front end and start creating the UIs needed to dispatch actions unto our MongoDB + Node.JS + Express.JS system.

Aww, yeah!!!!

Go back to /client/src/App.js and apply the following changes.
“React Rocks”

Lastly, we edit our front end’s package.json and add a proxy there to point to the port where our back end is deployed.

Remember, this is our front end’s package.json so this is included inside the client directory. Edit that there.

There, all that’s left to do is to make it so that we can launch our back end then our front end at the same time.

In order to do that go back to the main directory of our project and type the following:

npm init -y
npm i -S concurrently

Edit the package.json of our main project’s directory. Change it as follows.

Here, you can see under the “scripts” key, the “start” key makes use of the package we just installed, the concurrently package. That package enables us to run the back end code using:

node server.js

And the front end code using:

npm start

There’s a lot happening under the hood in able to do this, but for now, we will just leave it be and be happy that it works! Now, to start our app just go to the main directory of our project then type:

npm start

A browser will open that contains our app and voila! We have made our own MERN (FULL STACK) app from scratch! Feel free to play around with it. Use it as a sand box to grasp the different concepts of both ends here.

Oh, and one more thing. Make sure to enable CORS on your browser since we are calling our own APIs via our own machine. Here is a great plug-in to do just that. 😬

As promise, here is the git repo.
That’s All Folks, cheers!

I hope that I have provided clear instructions and that I was able to transfer as much knowledge as I can, to you, the reader.

If you found this useful, be sure to leave some claps! Oh, and share it on your social platforms too! :)
