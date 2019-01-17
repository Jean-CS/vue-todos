# vue_todos

v-bind:object
v-bind:class

## Event Handler

v-on:change

## Emitting Events

`@click="$(emit('del-todo', todo.id))"`

This will emit an event with:

```javascript
name: 'del-todo',
type: '$emit',
source: '<TodoItem>',
payload: [
    1,
]
```

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Run your tests

```
npm run test
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).
