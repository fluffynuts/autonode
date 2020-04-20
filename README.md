# autonode

## What?
leverages off of nvm to automatically provide the required node version to run a node app

## Usage
### By script name
copy / symlink this with the required node version appended to the script name, eg
```sh
# once-off
cp autonode autonode-12.16.1
# or
ln -s /path/to/autonode autonode-12.16.1
# run app.js with node version 12.16.1
./autonode-12.16.1 app.js
```
### By environment variable
set NODE_VERSION and execute:
```sh
# run app.js with node version 12.16.1
NODE_VERSION=12.16.1 ./autonode app.js
```

## Why?
- NVM is awesome
- Node versioning can be an issue: for example, a project built around node 8, which is to be upgraded to node 12, 
  where changes have to be made to go either way. When deploying, NVM would be nice to use here, but we don't want
  to set NVM to spawn the same version of node for everyone (just yet)
  - basically, I wanted to upgrade a node 8 project to node 12 without causing system-wide or even shell-wide impact

## How?
- install NVM if it's not already available
- determine the node version from file name or environment variable
- ask NVM where the required version is
- if it's missing, go get it
- invoke the correct version with the rest of the CLI parameters

## Windows?
Perhaps, if I need to. Right now, this will only be a shell script that can be used on a *nix-ey system (or WSL, I guess)
