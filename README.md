# SAD (NYC) Matching app

This is a MongoDB backed node express react app intended to be deployed via 
Heroku.  

You must have node (v12) and docker installed.

## Development
Folder is configured with server yarn packages in `package.json`.  Do not
use NPM commands, and delete `package-lock.json` if it exists.

Server folder contains server source and client folder contains client source.
Note that client folder contains its own `package.json` file and also uses yarn,
though generally you should use the provided scripts to interact with the 
client.

### Setup
```
git clone <repository URL>
cd sadnyc
yarn install
```

### Useful scripts
```
## Dev docker workflow 
## - Starts up local mongo instance on port 27017
## - Starts up server on https://localhost:5000
## - Starts up dev client server on http://localhost:3000
yarn dev

## Low level (to develop locally outside docker):
yarn install # install dependencies

yarn server # start the server (https://localhost:5000)
yarn client # start local client server (http://localhost:3000)

yarn lint # lint and fix code with eslint
yarn test # run jest tests

yarn start # build client assets and serve production-like server
```

Development deploys will watch for changes so there is no need to restart
the servers, unless Dockerfiles or package.json files are changed.

!!Important:
Local development with HTTPS is provided using the devcert library.
As such, running the application for the first time will prompt you for your
system password so that it can install a local certificate to your keychain.
Note that some browsers will not accept the local certificate anyway, and will
explicitly ask if you want to proceed to the site.  Since this is a development
server it is safe to do so, but never do this if you see the warning on a real 
website.
