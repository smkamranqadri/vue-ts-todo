<template>
  <div>
    <todo :todo="todo" :editTodo="editTodo" :addTodo="addTodo"></todo>
    <ul>
      <li v-for="(todo, index) in todos" v-bind:key="todo">
        {{todo}}
        <button v-on:click="showEdit(todo, index)">
          e
        </button>
        <button v-on:click="removeTodo(todo)">
          x
        </button>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Component from 'vue-class-component';

import Todo from '../components/todo.vue';

@Component({
  components: {
    Todo
  }
})
export default class Todos extends Vue {
  todos: Array<string>;
  todo = {
    text: '',
    index: undefined
  };

  constructor() {
    super();
    this.todos = ['Task 1', 'Task 2', 'Task 3'];
  }

  created() {
    console.log('created!')
  }

  addTodo(todo: string) {
    console.log('parent todo', todo);
    this.todos.push(todo);
    this.todo.text = '';
    this.todo.index = undefined;
  }

  showEdit(todo, index) {
    this.todo.index = index;
    this.todo.text = todo;
  }

  editTodo(todo, index) {
    console.log('todo', todo);
    console.log('index', index);
    this.todos.splice(index, 1, todo);
    this.todo.text = '';
    this.todo.index = undefined;
  }

  removeTodo(todoToRemove) {
    console.log('removeTodo!', todoToRemove);
    this.todos = this.todos.filter(todo => todo !== todoToRemove);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
