<template>
  <div id="app">
    <div class="container">
      <h1 class="text-center mb-4">todo list</h1>

      <input type="text" class="form-control" v-model="userInput" @keyup.enter="addNewTodo">

      <ul class="list-group mb-4">
        <li class="list-group-item text-left" v-for="todo in activeTodoList" v-bind:key="todo.index" v-on:click="toggleTodoState(todo)">
          {{ todo.label }}
        </li>
      </ul>

      <div class="text-right">
        <button type="button" class="btn btn-sm" v-on:click="changeCurrentState('active')">미래</button>
        <button type="button" class="btn btn-sm" v-on:click="changeCurrentState('done')">과거</button>
        <button type="button" class="btn btn-sm" v-on:click="changeCurrentState('all')">전체</button>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      userInput: '',
      todoList:[]
    };
  },
  computed: {
    activeTodoList() {
      return this.todoList.filter(todo => this.currentState === 'all' || todo.state === this.currentState);
    }
  },
  methods: {
    changeCurrentState(state){
      this.currentState = state;
    },
    addNewTodo() {
      this.todoList.push({
        label : this.userInput,
        state : 'active'
      });
      this.userInput = '';
    },
    toggleTodoState(todo){
      todo.state = todo.state === 'active' ? 'done' : 'active';
    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
