<template>
  <div>
    <div :key="todo.id" v-for="todo in todos">
      <ToDoItem :todo="todo" />
    </div>
    <form v-if="newItem">
      <input type="text" v-model="task" placeholder="Enter a new todo...">
      <input type="submit" @click="newTodo" value="Add Todo">
    </form>
    <button v-if="!newItem" @click="addTodoInput">Add New Todo</button>
  </div>
</template>

<script>
import ToDoItem from './ToDoItem.vue'

export default {
  components: {
    ToDoItem
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          task: "Finish homework",
          complete: true
        },
        {
          id: 2,
          task: "Wash dishes",
          complete: true
        },
        {
          id: 3,
          task: "Workout",
          complete: true
        }
      ],
      newItem: false
    }
  },
  methods: {
    addTodoInput() {
      this.newItem = true;
    },
    newTodo(e, task) {
      e.preventDefault;

      this.newItem = false;
      let todo = {
        id: (this.todos.length + 1),
        task: this.task,
        complete: false
      };

      this.todos = [...this.todos, todo];

      this.task = "";
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less"></style>