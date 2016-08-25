
#### Basic


- Download and extract http://aurelia.io/downloads/basic-aurelia-project.zip

You can also follow the tutorial here: http://aurelia.io/hub.html#/doc/article/aurelia/framework/latest/quick-start/1

---

Add todo.ts into a src folder:
    [lang=js]
    export class Todo {
    done = false;

    constructor(public description: string) { }
    }

---

Add an app.ts file into src:

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

Add an main.ts file to src:
    [lang=js]
    import {Aurelia} from 'aurelia-framework';

    export function configure(aurelia: Aurelia) {
    aurelia.use.basicConfiguration();
    aurelia.start().then(() => aurelia.setRoot());
    }

---

Add an app.html file to src:
    [lang=html]
    <template>
    <h1>${heading}</h1>
    </template>

---

### Fire it up
- with nodejs (must install node.js first if it does not exist)
- npm install http-server -g
- http-server -o -c-1

#### Alternativly do it from VS:
Visual Studio - Open Visual Studio 2015. Using the main menu, select File > Open > Web site... In the resulting dialog, choose the project folder then click the Open button. The folder contents will be displayed in the Visual Studio Solution Explorer window. Right click on index.html in Solution Explorer and select "View in Browser". This will fire up IISExpress and serve index.html.

---
Change app.html

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

Change app.html
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

Change app.html
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

Checkout the contactmanager tutorial for a lot more fun features: http://aurelia.io/hub.html#/doc/article/aurelia/framework/latest/contact-manager-tutorial
