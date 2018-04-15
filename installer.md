# INSTALL NOTES

## Upgrading Node with Chocolatey (run from admin shell)

choco upgrade nodejs.install -y

### When an upgrade isn't sufficient, we can use

choco install nodejs.install --force -y

## Updating NPM

npm i -g npm

## Installing Typescript and TSLint

npm install -g tslint typescript

## Installing ts2Fable

npm install -g ts2Fable

and, for the new version,

npm install -g ts2Fable@next

## Creating the babylonfs.fs file (calling from the application root directory)

ts2fable node_modules\babylonjs\babylon.d.ts projects\bblyn\babylonjs.fs










