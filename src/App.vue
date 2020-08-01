<template>
  <div id="app">
    <Header/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    <AddTodo v-on:add-todo="addTodo"/>
  </div>
</template>

<script>
import Todos from './components/Todos';
import Header from './components/Header';
import AddTodo from './components/AddTodo';

export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data(){
    return{
      todos:[]
    }
  },
  methods:{
    deleteTodo(id){
      this.todos = this.todos.filter((todo)=> todo.id !== id);
    },
    addTodo(title){
      const id = this.todos.length + 1;
      this.todos = [...this.todos,{id,title,completed:false}];
    }
  },
  async created(){
    try{
      const response = await fetch("https://jsonplaceholder.typicode.com/todos?_limit=5");
      const result = await response.json();
      this.todos = result;
    }catch(error){
      console.log(error);
    }
  }
}
</script>

<style>

*{
  margin:0;
  padding:0;
  box-sizing: border-box;
}

</style>
