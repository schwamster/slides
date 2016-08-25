- title : Aurelia
- description : Introduction to Aurelia
- author : Bastian Töpfer
- theme : night
- transition : default

***

### What is Aurelia?

![FsReveal](images/main-logo.svg)

V1 since 27th of July 2016

***

### Why bother?

- NG1 is from 2010, most of the akward ways are obsolete (ES2015/2016)
- Steep learning curve and litte team knowglede present
- Known Performance issues - watchers (obsolete dirty checking)
- techical debt build up since 2010
' modules, pure HTML5 custom (web) components, shadow DOM that, two-way data binding using Object.observe.
' new concepts:one-time data binding, controllerAs, bindToController - old concepts like $scope

=> Still have time to change!

***

### Aurelia is/has
- a medium size framework with no external dependencies.
- as fast or faster than all other frameworks.
- more standards compliant than most other frameworks.
- he most unobstrusive framework today.
- integrates very well with other libraries. Other frameworks like Angular and React have a harder time with this.
- has the best support for separated presentation patterns (MVC, MVVM, MVP)
- is better at dynamic, data-driven UI construction than anything else today.
- is written in 100% ES 2015/2016, no dependencies except polyfills.
- no unnecessary DOM abstractions. faster and consume less memory
- some of the best support for Web Components.
- the only framework built with a modern, modular architecture.

***

### Other Choices

- Angular 1
- Angular 2
- Ember
- Polymer
- React

***

### How do they compare?

#### Size
![FsReveal](images/size.png)

---

#### Performance
![FsReveal](images/performance.png)

---

#### Standard Compliance
![FsReveal](images/standard-compliance.png)

---

#### Obtrusiveness
![FsReveal](images/obtrusiveness.png)

---

#### Interoperability
![FsReveal](images/interoperability.png)

---

#### Separated Presentation
![FsReveal](images/separated-presentation.png)

---

#### Project
![FsReveal](images/project.png)

---

#### Community
![FsReveal](images/community.png)

---

#### Core Team
![FsReveal](images/core-team.png)

---

#### Learning Materials
![FsReveal](images/learning-materials.png)

---

#### Business
![FsReveal](images/business.png)

---

#### What to choose?
![FsReveal](images/what-to-choose.png)

***
### Tutorials

***
#### Basic


- Download and extract http://aurelia.io/downloads/basic-aurelia-project.zip

You can also follow the tutorial here: http://aurelia.io/hub.html#/doc/article/aurelia/framework/latest/quick-start/1

---

### Add todo.ts into a src folder:

    [lang=js]
    export class Todo {
    done = false;

    constructor(public description: string) { }
    }

---

### Add an app.ts file into src:

    [lang=js]
    import {Todo} from './todo';

    export class App {
    heading = "Todos";
    todos: Todo[] = [];
    todoDescription = '';

    addTodo() {
        if (this.todoDescription) {
        this.todos.push(new Todo(this.todoDescription));
        this.todoDescription = '';
        }
    }

    removeTodo(todo) {
        let index = this.todos.indexOf(todo);
        if (index !== -1) {
        this.todos.splice(index, 1);
        }
    }
    }

---

### Add an main.ts file to src:
    [lang=js]
    import {Aurelia} from 'aurelia-framework';

    export function configure(aurelia: Aurelia) {
        aurelia.use.basicConfiguration();
        aurelia.start().then(() => aurelia.setRoot());
    }

---

### Add an app.html file to src:
    [lang=html]
    <template>
        <h1>${heading}</h1>
    </template>

---

### Fire it up
#### with nodejs (must install node.js first if it does not exist)
    
    npm install http-server -g
    http-server -o -c-1

#### Alternativly do it from VS:
Visual Studio - Open Visual Studio 2015. Using the main menu, select File > Open > Web site... In the resulting dialog, choose the project folder then click the Open button. The folder contents will be displayed in the Visual Studio Solution Explorer window. Right click on index.html in Solution Explorer and select "View in Browser". This will fire up IISExpress and serve index.html.

---

### Change app.html

    [lang=html]
    <template>
    <h1>${heading}</h1>

    <form submit.trigger="addTodo()">
        <input type="text" value.bind="todoDescription">
        <button type="submit">Add Todo</button>
    </form>
    </template>
' different binding modes. .bind auto - e.g. two way for forms. => one-way, two-way one-time

---

### Change app.html
    [lang=html]
    <template>
    <h1>${heading}</h1>

    <form submit.trigger="addTodo()">
        <input type="text" value.bind="todoDescription">
        <button type="submit">Add Todo</button>
    </form>

    <ul>
        <li repeat.for="todo of todos">
        <input type="checkbox" checked.bind="todo.done">
        <span>
            ${todo.description}
        </span>
        <button click.trigger="removeTodo(todo)">Remove</button>
        </li>    
    </ul>
    </template>

---

### Change app.html
    [lang=html]
    <template>
    <h1>${heading}</h1>

    <form submit.trigger="addTodo()">
        <input type="text" value.bind="todoDescription">
        <button type="submit">Add Todo</button>
    </form>

    <ul>
        <li repeat.for="todo of todos">
        <input type="checkbox" checked.bind="todo.done">
        <span css="text-decoration: ${todo.done ? 'line-through' : 'none'}">
            ${todo.description}
        </span>
        <button click.trigger="removeTodo(todo)">Remove</button>
        </li>    
    </ul>
    </template>
---

### Checkout the contactmanager tutorial for a lot more fun features: http://aurelia.io/hub.html#/doc/article/aurelia/framework/latest/contact-manager-tutorial

---

***
### The Cli Tools

- install node js
- install git client

- install the aurelia cli tools: npm install aurelia-cli -g

![FsReveal](images/cli-tools.png)


***
### Sources
- https://medium.com/hashnode-insights/rob-eisenberg-on-aurelia-and-how-it-stacks-up-against-angular-2-and-react-82721d714449#.9tcphmfxi
- https://www.youtube.com/watch?v=PrNYL42x85o or a neutral write up of Kevin O'Shaughnessy https://medium.com/@ZombieCodeKill/choosing-a-javascript-framework-535745d0ab90#.6bjpyzv99
- https://www.youtube.com/watch?v=gkbZ1LpWQB4#t=469.223226
- http://aurelia.io 
- http://www.dotnetrocks.com/?show=1279 (podcast)
- http://www.ae.be/blog-en/comparing-angular-aurelia-react-js-framework/
- https://altabel.wordpress.com/2016/03/15/aurelia-as-a-next-generation-ui-framework-comparison-of-aurelia-angular-and-react-js/
- http://blog.durandal.io/2015/03/16/aurelia-and-angular-2-code-side-by-side/
- http://blog.durandal.io/2015/03/17/aurelia-angular-2-0-code-side-by-side-part-2/



***

### The Reality of a Developer's Life 

**When I show my boss that I've fixed a bug:**
  
![When I show my boss that I've fixed a bug](http://www.topito.com/wp-content/uploads/2013/01/code-07.gif)
  
**When your regular expression returns what you expect:**
  
![When your regular expression returns what you expect](http://www.topito.com/wp-content/uploads/2013/01/code-03.gif)
  
*from [The Reality of a Developer's Life - in GIFs, Of Course](http://server.dzone.com/articles/reality-developers-life-gifs)*

