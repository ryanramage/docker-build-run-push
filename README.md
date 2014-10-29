docker-build-tag-push
======================

An easy way to excute the typical sequence of commands to build, tag and push a node project
to a private repo.

Usage
-----

in your project, execute

    npm install docker-build-tag-push

add the following to your package.json

      "docker-registry": "docker.your-private.com",

and

       "scripts": {
        "docker": "./node_modules/.bin/docker-build-tag-push",
      },

Now in your project, when you are ready bump your version number in package.json then run


    npm run docker

