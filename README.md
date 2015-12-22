docker-build-run-push
=====================

An easy way to excute the typical sequence of commands to build, run and push a node project
to a private docker repo.

Usage
-----

in your project, execute

    npm install docker-build-run-push --save

add the following to your package.json

      "docker-registry": "docker.your-private.com",

and add some scripts that look like this. You might adjust to your liking

       "scripts": {
		    "docker-build": "rm -rf node_modules && npm i --production && docker-build",
		    "docker-run": "docker-run",
		    "docker-push": "rm -rf node_modules && npm i --production && docker-push",
      },

Now in your project, when you are ready bump your version number in package.json.

To build a local docker image quickly, for running later

    npm run docker-build

Run the local docker image just built

    npm run docker-run

Push the docker image to the docker-registry specified in your package.json

    npm run docker-push

