docker-build-run-push
=====================

npm scripts to automate docker images. 

An easy way to excute the typical sequence of building, running and pushing a docker image out of a node project to a private docker repo,
or the public docker hub.

Uses the name and version number from package.json to keep your docker image name and version aligned.

Usage
-----

in your project, execute

    npm install docker-build-run-push --save

If you are pushing to a private docker repo, add the following to your package.json

      "docker-registry": "docker.your-private.com",

Or if you are pushing to the public docker hub, add the following to your package.json

    "docker-user": "ryanramage".

Add some scripts that look like this. You might adjust to your liking

      "scripts": {
		    "docker-build": "rm -rf node_modules && npm i --production && docker-build",
		    "docker-run": "docker-run",
		    "docker-push": "docker-push",
      },

Now in your project, when you are ready to make a new image, bump your version number in package.json.

To build a local docker image quickly, for running later

    npm run docker-build

Run the local docker image just built

    npm run docker-run

Push the docker image to the docker-registry specified in your package.json

    npm run docker-push


## docker-run arguments

It's common to have to pass arguments when running a docker. The '+' character to split the arguments for the docker command.

Here are some example of what they mean


Run a different command in the docker image then the CMD specified

    npm run docker-run — node ./bin/cli.js


Pass a port and an env file as arguments.

    npm run docker-run -- -p 3000:3000 --env-file .env + 

Start an interactive terminal

    npm run docker-run -- -i -t + /bin/bash

