<!--Raul Garcia-->
<!-- Credit: Traversy Media: Vue JS Crash Course-->

<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <!--{{}} -->
    <!--Embeded Compoenent -->
    <!--Vue template directive <vibind> passed in as a prop-->
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
import axios from 'axios';

export default {
  name: 'app',
  components: {
    Header,
    AddTodo,
    Todos
  },
    //function that returns an object
    data(){
      return{
        //Array of objs similar to React array <vue framework>
        todos:[]
      }
    },
    methods: {
      deleteTodo(id){
        this.todos = this.todos.filter(todo => todo.id !==id);
      },
      addTodo(newTodo) {
        const {title,completed} = newTodo;
        axios.post('https://jsonplaceholder.typicode.com/todos',{
          title,
          completed
        })
        .then(res => this.todos = [...this.todos, res.data])
        //.catch(console.error("error"));
      }
    },
    //Install axios api on terminal...
    //http lib to get, post etc... req
    created() {
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      //.catch(console.error("error"));
      }
  }

</script>

<style>
    *{
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: Ariel, Helvetica, sans-serif;
      line-height: 1.4;
    }

    .btn {
      display: inline-block;
      border: none;
      background: #555;
      color: #fff;
      padding: 7px 20 px;
      cursor: pointer;
    }

    .btn:hover {
      background: #666;
    }
</style>
