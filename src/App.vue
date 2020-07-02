<template>
    <div id="app">
        <AddTodo @add-todo="addTodo"></AddTodo>
        <TodoList
                v-if="todos.length"
                v-bind:todos="todos"
                @remove-todo="removeTodo"

        />
        <p v-else>No todos</p>

    </div>
</template>

<script>
import TodoList from '@/components/TodoList.vue';
import AddTodo from '@/components/AddTodo.vue';
export default {
  name: 'App',
    data() {
      return {
          todos: [
              {id: 1, title: 'task1', completed: false},
              {id: 2, title: 'task2', completed: false},
              {id: 3, title: 'task3', completed: false}

          ]
      }
    },
    methods: {
      removeTodo(id) {
          console.log(id)
          this.todos = this.todos.filter(t => t.id !== id)

      },
        addTodo(todo) {
          console.log(todo)
          this.todos.push(todo)
        }

    },
  components: {
    TodoList, AddTodo
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
  margin: 20%;
  transform: translate(-50% -50%);
}
</style>
