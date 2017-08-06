# hapi-sleep

This is a plugin for [hapi](hapijs.com) to generate an [insomnia](insomnia.rest) workspace at start time.  This plugin exposes an endpoint `/insomnia` that returns an insomnia import/export JSON string.  This plugin is meant to be used by importing from a link in insomnia.  

![import](https://raw.githubusercontent.com/jaywunder/hapi-sleep/master/imgs/importexport.png)

hapi sleep currently takes all the routes on your server given a baseurl, and makes folders and routes that correspond to your route structure.  Currently hapi-sleep does not know about route parameters (`/api/v1/user/{id}`).

# Usage

```bash
npm install hapi-sleep --save

# start your server

curl localhost:3000/insomnia
```

```javascript
server.register({
  register: require('hapi-sleep'),
  options: {
    baseUrl: '/api/v1',
    name: 'Example Project'
  }
}, () => { /* ... */ })
```
# Roadmap

 - Make more settings
 - Integrate with validations to make default query and body
 - Integrate with docs in hapi and description in insomnia
 - Develop an insomnia plugin that live watches the hapi-sleep route and and imports new routes on the fly

# Contributing

If you'd like to contribute:

 - fork the master branch
 - write code
 - make a pull request

If you have a feature request then feel free to make an issue
