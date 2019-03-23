<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <div class="wrap">
      <TodoInput v-on:addTodo="addTodo"></TodoInput>
      <TodoList v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></TodoList>
      <TodoFooter v-on:removeAll="removeAll"></TodoFooter>
    </div>
  </div>
</template>6

<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
import TodoFooter from "./components/TodoFooter.vue";

export default {
  data() {
    return {
      todoItems: []
    }
  },
  methods: {
    addTodo(todoItem) {
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    removeAll() {
      localStorage.clear();
      this.todoItems = [];
    }
  },
  components: {
    "TodoHeader": TodoHeader,
    "TodoInput": TodoInput,
    "TodoList": TodoList,
    "TodoFooter": TodoFooter
  },
  created() {
    if (localStorage.length > 0) {
        for (let i = 0; i < localStorage.length; i++) {
            let localKey = localStorage.key(i);
            if (localKey === "loglevel:webpack-dev-server") continue;
            this.todoItems.push(localStorage.key(i));
        }
    }
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
  padding: 0 10px;
}
</style>
