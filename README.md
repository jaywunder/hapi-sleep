# hapi-sleep

This is a plugin for [hapi](hapijs.com) to generate an [insomnia](insomnia.rest) workspace at start time.  This plugin exposes an endpoint `/insomnia` that returns an insomnia import/export JSON string.  This plugin is meant to be used by importing from a link in insomnia.  

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
    name: 'Example Project',
    forEach(resource, route) { /* ... */ }
  }
}, () => { /* ... */ })
```

**warning** hapi-sleep reserves the endpoint name `_index` for a route that also has subroutes. i.e. `/users/` and `/users/create`. The `/users/` endpoint would be in a folder called `users` in a route called `_index`.

![import export insomnia](https://github.com/jaywunder/hapi-sleep/blob/master/imgs/importexport.png)

# Options

- `baseUrl` the base url that hapi-sleep should look for routes
- `name` The name of the insomnia workspace
- `log` whether to log where you can import the insomnia file from at startup time
- `environment` JSON object with variables that you'd like in your environment.  hapi-sleep already defines a variable `api` which points to your server url and the baseUrl
- `forEach(resource, route)` Resource will go to the insomnia server, and route is the route from your hapi server.  You should mutate the resource in place and not return anything

# Roadmap

 - Integrate with validations to make default query and body
 - Integrate with docs in hapi and description in insomnia
 - Develop an insomnia plugin that live watches the hapi-sleep route and and imports new routes on the fly

# Contributing

If you'd like to contribute:

 - fork the master branch
 - write code
 - make a pull request

If you have a feature request then feel free to make an issue
