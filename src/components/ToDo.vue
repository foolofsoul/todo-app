<template>
  <div class="todo-main">
    <div :key="todo.id" v-for="todo in todos">
      <ToDoItem :todo="todo" @update-task="updateTask" />
    </div>
    <button
      v-if="!newItem"
      class="button button--action"
      @click="addTodoInput"
    >
      <i class="fas fa-plus"></i>Add Task
    </button>
    <ToDoInput v-else @close="closeInput" @update-todos="updateTodos"/>
  </div>
</template>


<script>
import ToDoItem from './ToDoItem.vue';
import ToDoInput from './ToDoInput.vue';

export default {
  components: {
    ToDoInput,
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
    },

    updateTodos(todo) {
      this.todos = [...this.todos, todo];
    },

    updateTask(todo) {
      let todoIndex = this.todos.findIndex((task) => todo.id === task.id);
      this.todos[todoIndex].task = todo.task;
    },

    closeInput() {
      this.newItem = false;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
  .todo-main {
    background: #ffffff;
    padding: 32px;
    border-radius: 4px;
    box-shadow: 0px 2px 15px rgba(0, 0, 0, 0.05);
  }
</style>