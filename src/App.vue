<template>
  <div class="container">
    <h2 class="title">Plan your day</h2>
    <div class="wrapper">
      <FormHeader />
      <TodoForm @todo-submition="addTodos"/> 
      <TodoList v-if="todoList.length" :todoList="todoList" :removeTodos="removeTodos" />
      <FormFooter :todoList="todoList" />
    </div>
  </div>
</template>

<script>
import TodoForm from './components/TodoForm.vue'
import TodoList from './components/TodoList.vue'
import FormHeader from './components/FormHeader.vue'
import FormFooter from './components/FormFooter.vue'

export default {
  name: 'App',
  components: {
    TodoForm,
    TodoList,
    FormHeader,
    FormFooter
  },
  data: () => {
    return {
      todoList: []
    }
  },
  methods: {
    addTodos(todo) {
      this.todoList.push(todo)
    },
    removeTodos(index) {
      this.todoList.splice(index, 1)
      console.log(this.todoList)
    }
  }
}
</script>

<style>
body {
    font-family: Inter, Roboto, Oxygen, Fira Sans, Helvetica Neue, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-size: 16px;
    background: #F3F3EE;
}

.container {
  margin-right: auto;
  margin-left:  auto;
  max-width: 960px;
}

.wrapper {
  max-width: 500px;
  margin: 40px auto;
  padding: 2rem;
  background: #ffffff;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 1px 3px 0px, rgba(0, 0, 0, 0.06) 0px 1px 2px 0px;
}

#app {
  text-align: center;
  margin-top: 60px;
  padding-right: 10px;
  padding-left:  10px;
}

h2, label {
    color: #2c3e50;
}

.title{
  text-transform: uppercase;
  font-size: 2.7rem;
  margin: 4rem 0;
}
</style>
