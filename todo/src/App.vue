<template>
<div id="app">
  <div class="container col-sm-6 offset-md-3">
    <TodoHeader v-on:addTodo="addTodo"></TodoHeader>
    <TodoList v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></TodoList>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</div>
</template>

<script>
import TodoHeader from './components/TodoHeader';
import TodoList from './components/TodoList';
import TodoFooter from './components/TodoFooter';

export default {
  data() {
    return {
      todoItems: [],
      isActive: false
    }
  },
  created() {
      if(localStorage.length > 0){
          for(let i = 0; i < localStorage.length; i++){
              if(localStorage.key(i) != "loglevel:webpack-dev-server"){
                  this.todoItems.push(localStorage.key(i));
              }
          }
      }
  },
  methods: {
    addTodo(todoItem){
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    removeTodo(todoItem, index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    clearAll(){
      localStorage.clear();
      this.todoItems = [];
    }
  },
  components: {
    'TodoHeader': TodoHeader,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter
  }
}
</script>

<style>

body{
background: #3E4651;
}

.hidden{
position: absolute;
visibility: hidden;
text-indent: -9999px;
}
#app{
font-family: 'Noto Sans KR', sans-serif;
}

.container{
max-width: 40%;
margin:1.5rem auto;
padding:1.5rem 0;
background: #00B5B5;
}

</style>
