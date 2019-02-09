<template>
  <div class="App">
    <div class="header">
      <h1>오늘 뭐할까?</h1>
    </div>
    <create-form v-on:update="handleCreate"/>

    <div class="white-box">
      <todo-list :todos="todos" v-on:onCheck="handleCheck" v-on:onRemove="handleRemove"/>
    </div>
  </div>
</template>

<script>

  import CreateForm from './components/CreateForm';
  import TodoList from './components/TodoList';

  export default {
    name: 'app',
    components: {
      'create-form': CreateForm,
      'todo-list': TodoList,
    },
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
        id: 3,
        todos: [
          {
            id: 0,
            text: '앵귤러 배우고',
            checked: true
          },
          {
            id: 1,
            text: '리액트 배우고',
            checked: false
          },
          {
            id: 2,
            text: '뷰 배우고',
            checked: false
          }

        ]
      }
    },
    methods: {
      handleCheck(id){
        this.todos = this.todos.map((todo)=>{
          if(todo.id === id) return {...todo, checked: !todo.checked}
        return todo
      })
      },
      handleCreate(text) {
        // this.todos = [...this.todos, {
        //   id: this.id ++,
        //   text: text,
        //   checked: false
        // }]
        this.todos = this.todos.concat({
          id: this.id++,
          text: text,
          checked: false
        })
      },
      handleRemove(id){
        this.todos = this.todos.filter(todo=>todo.id !== id)
      },
    },
    watch: {
      todos: {
        handler() {
          console.log('Todos changed!');
          localStorage.setItem('todos', JSON.stringify(this.todos));
        },
        deep: true,
      },
    },

    mounted() {
      console.log('App mounted!');
      if (localStorage.getItem('todos')) this.todos = JSON.parse(localStorage.getItem('todos'));
    },

  }
</script>
<style>
  .App{width: 600px;margin: 0 auto;}
</style>
