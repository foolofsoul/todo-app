<template>
  <div>
    <div :key="todo.id" v-for="todo in todos">
      <ToDoItem :todo="todo" />
    </div>
    <form v-if="newItem">
      <input
        type="text"
        ref="todoInput"
        v-model="task"
        placeholder="Enter a new todo...">
      <button @click.prevent="newTodo">Add Todo</button>
      <button @click.prevent="closeTodo">Close</button>
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
      newItem: false,
      task: ""
    }
  },

  methods: {
    addTodoInput() {
      this.newItem = true;
      this.$nextTick(() => this.$refs.todoInput.focus());
    },

    newTodo() {
      let todo = {
        id: (this.todos.length + 1),
        task: this.task,
        complete: false
      };

      this.todos = [...this.todos, todo];
      this.task = "";
      this.closeTodo();
    },

    closeTodo() {
      this.newItem = false;
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
  form {
    display: inline-block;
    padding: 16px;
    background-color: #f8fafb;
  }
</style>