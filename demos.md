
# Demos

## CSS Framework

Bulma (https://bulma.io/)

## API Server

json-server (https://github.com/typicode/json-server)

Setup
  Create db.json file
  `npx json-server --watch db.json`

Browse to an endpoint

### React CLI

[User Guide](https://github.com/facebook/create-react-app/blob/master/packages/react-scripts/template/README.md)

#### Getting Started

No install necessary!

##### Project Creation

```
npx create-react-app my-app
cd my-app
npm start
```

##### Project Layout

* HTML file
* App mounting
* Component files

##### Dev Workflow

* `npm start`
* Make changes, review in the browser, and repeat!

#### Basic Components

* Everything is a component in React
* Two types of components
  * Stateless function components
  * Stateful class components

##### JSX

* JSX is not HTML!
* Element attributes mirror their JavaScript elememt properties
* How to create elements
* How to set element attribute values
* How to handle events

##### Props

* Props are readonly!

##### State

* State must not be directly mutated
* Use `setState()` to mutate the state object

#### Basic Task

* Use `componentDidMount()` method to make API call
* Set state
* Render the list

#### Completed App

Other highlights in the final code...

* React encourages you to break your UI down into smaller and smaller components
* Getting the hang of JSX can take a little while... but it's not too bad

#### Production Build

* `npm run build`
* How big are the bundled file(s)?

### Angular CLI

[https://cli.angular.io/](https://cli.angular.io/)

#### Getting Started

```
npm install -g @angular/cli
```

##### Project Creation

```
ng new my-app
cd my-app
ng serve
```

##### Project Layout

* HTML file
* App mounting
* Module
* Component files

##### Dev Workflow

* `ng serve`
* Make changes, review in the browser, and repeat!

#### Basic Components

##### Modules and Components

Angular gives you a container for your components
  You can think of the module conceptually as an assembly
  You can share modules across apps
  You can control the visibility of components within a module

##### Decorators

Decorators are similar to C# attributes... but much more powerful
They're more than just metadata
They can also modify your code

##### Services and DI

Angular is also the only framework of the three that has a formal notion of a "service"
And it's the only one that provides a DI container

```
ng generate service services/data --module app.module.ts
```

##### RxJS

Yet-another-thing-to-learn :)

##### Testing

Supports unit testing and e2e testing using Protractor

##### Templating

Attribute binding `[alt]="altText"`
Event binding `(click)="handleClick()"`

##### Properties

`@Input() name: string;`

##### Events

`@Output() onSearch = new EventEmitter<SearchCriteria>();`

#### Basic Task

* Make an API call using the Angular HttpClient in the `ngOnInit()` method
* Set the component property

```
ngOnInit(): void {
  const categories = this.dataService.getCategories();
  const albums = this.dataService.getAlbums();

  forkJoin([categories, albums]).subscribe(results => {
    this.categories = results[0];
    this.albums = results[1];

    this.resetSearchResults();
  });
}
```

#### Completed App

Other highlights in the final code...

* There's a lot of ceremony in an Angular app
* TypeScript really makes it feel like your writing C#... though you're not!
* The CLI is the most capable of the three CLIs
  * You can not only create your app but also add components and services

#### Production Build

* `ng build --prod`
* How big are the bundled file(s)?

### Vue (downgraded experience)

#### Getting Started

No install necessary!

##### Project Creation

Just create an HTML file!

```
<html>

<head>
</head>

<body>
  <div id="app">
    <h2 v-text="appName" v-once></h2>
  </div>

  <script src="https://unpkg.com/vue@2.5.13/dist/vue.js"></script>
  <script>
    var app = new Vue({
      el: '#app',
      data: {
        appName: 'Our Awesome App!'
      }
    });
  </script>
</body>

</html>
```

##### Project Layout

* The Vue instance
* The mounting point in the HTML becomes your template

##### Dev Workflow

* Make changes to your code
* Run a local server... I like `http-server`
* Refresh the page in the browser

#### Basic Components

* Let's hold off on using components for a bit...
  * Well, other than our main component

##### Templating

##### Properties

##### Events

#### Basic Task

Make an API call and render a list

#### Completed App

Other highlights in the final code...

#### Production Build

* How big are the bundled file(s)?
  * What is the size of the CDN delivered minified library???

### Vue (downgraded experience... with components!)

Show passing values down to components
Show raising events to pass values up to parents

### Vue CLI (single file components and modules)

Docs: https://github.com/vuejs/vue-cli/blob/dev/docs/README.md

```
npm install -g @vue/cli
vue create demo
cd demo
npm run serve
```

#### Commands

create
invoke
inspect
serve
build
init

#### Single File Components

Drawbacks of global components
 * Global definitions force unique names for every component
 * String templates lack syntax highlighting and require ugly slashes for multiline HTML
 * No CSS support means that while HTML and JavaScript are modularized into components, CSS is conspicuously left out
 * No build step restricts us to HTML and ES5 JavaScript, rather than preprocessors like Pug (formerly Jade) and Babel

Other benefits of single file components
 * Complete syntax highlighting
 * CommonJS modules
 * Component-scoped CSS
   * CSS is extracted from each component and combined into a single resource
 * Precompiled templates
 
You can also use preprocessors such as Pug, Babel (with ES2015 modules), and Stylus for cleaner and more feature-rich components

One important thing to note is that separation of concerns is not equal to separation of file types

Even if you don’t like the idea of Single-File Components, you can still leverage its hot-reloading and pre-compilation features by separating your JavaScript and CSS into separate files:

```
<!-- my-component.vue -->
<template>
  <div>This will be pre-compiled</div>
</template>
<script src="./my-component.js"></script>
<style src="./my-component.css"></style>
```

#### Gotchas

* Install and configure VS Code Vue.js tooling
  * Vetur
* Static assets can be handled in two different ways:
  * Imported in JavaScript or referenced in templates/CSS via relative paths. Such references will be handled by webpack.
  * Placed in the public directory and referenced via absolute paths. These assets will simply be copied and not go through webpack.
