<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <div class="wrap">
      <TodoInput></TodoInput>
      <TodoList></TodoList>
      <TodoFooter></TodoFooter>
    </div>
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
import TodoFooter from "./components/TodoFooter.vue";

export default {
  components: {
    "TodoHeader": TodoHeader,
    "TodoInput": TodoInput,
    "TodoList": TodoList,
    "TodoFooter": TodoFooter
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  font-family: 'Gothic A1', sans-serif;
}

body {
  background-color: #cefbc9;
  text-align: center;
}

.wrap {
  padding: 0 0.8rem;
}
</style>
