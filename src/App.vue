<template>
  <div id="app">
    <FilterTodos />
    <Todos />
    <AddTodo />
    <Footer />
  </div>
</template>

<script>
import Todos from "./components/Todos"
import AddTodo from './components/AddTodo'
import FilterTodos from './components/FilterTodos'
import Footer from './components/Footer'

export default {
  name: "App",
  components: {
    Todos,
    AddTodo,
    FilterTodos,
    Footer
  },
};
</script>

<style>
html,body{
  min-height:100vh;
}
body {
  background: #e8f7f0;
}
</style>
