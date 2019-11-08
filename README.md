# stencil_cheats

## I want to include local component

Situation : I want to import local component "toto" into my component "toto_father" 

### With npm install

1. Build your local component with npm run build
```
cd <toto dir> 
npm run build
```
2. Modify toto_father package.json to install local component
```
"dependencies": {
    "toto": "file:<path to toto directory>"
    }
```
3. Run npm install
```
cd <toto_father dir>
npm install
```
### I don't want to reinstall toto each time I change something inside

Build toto with watching, and use npm link
1. Build toto
```
cd <toto dir>
npm run build --watch
```

2. Npm link
```
cd <toto dir>
npm link # will create symlink in global node modules
cd <toto_father dir>
npm link toto # will create symlink in node_module which reference global toto module
```
You still have to relaunch `npm start` in toto_father when you change something on toto because stencil doesn't seem to watch node_modules changes. 
