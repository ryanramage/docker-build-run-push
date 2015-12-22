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
		    "docker-push": "rm -rf node_modules && npm i --production && docker-push",
      },

Now in your project, when you are ready to make a new image, bump your version number in package.json.

To build a local docker image quickly, for running later

    npm run docker-build

Run the local docker image just built

    npm run docker-run

Push the docker image to the docker-registry specified in your package.json

    npm run docker-push

