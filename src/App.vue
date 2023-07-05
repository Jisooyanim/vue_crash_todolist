<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import AddTodo from './components/AddTodo'
import Header from './components/layout/Header';
import Todos from './components/Todos';

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo,
  },
  
  //Return an object
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Learn Vue",
          completed: true
        },
        {
          id: 2,
          title: "Had Breakfast",
          completed: true
        },
        {
          id: 3,
          title: "Die",
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      // ... ->spread operator, copy what is already in todos
      this.todos = [...this.todos, newTodo];
    },
  },
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn{
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn-hover{
    background: #666;
  }
</style>
