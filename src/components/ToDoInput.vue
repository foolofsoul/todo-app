<template>
  <form>
    <input
      type="text"
      autofocus
      placeholder="Enter a todo..."
      v-model="task">
    <button @click.prevent="addTask">{{ submitValue }} Task</button>
    <button @click.prevent="closeTodo">Close</button>
  </form>
</template>

<script>
export default {
  props: {
    editMode: {
      type: Boolean,
      default: false
    },

    todo: Object
  },

  data() {
    return {
      task: ''
    }
  },

  created() {
    if (this.todo) {
      this.task = this.todo.task;
    }
  },

  computed: {
    submitValue() {
      return !this.editMode ? "Add" : "Update";
    }
  },

  methods: {
    addTask() {
      if (this.editMode) {
        return this.editTask();
      }
      this.newTask();
    },

    newTask() {
      let todo = {
        id: (this.$parent.todos.length + 1),
        task: this.task,
        complete: false
      };

      this.$emit("update-todos", todo);
      this.closeTodo();
    },

    editTask() {
      this.$emit("update-task", { id: this.todo.id, task: this.task });
      this.closeTodo();
    },

    closeTodo() {
      this.$emit("close");
    },
  }
}
</script>

<style lang="less" scoped>
  form {
    display: inline-block;
    padding: 16px;
    background-color: #f8fafb;
  }
</style>
