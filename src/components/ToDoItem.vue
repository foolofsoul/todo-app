<template>
  <div>
    <div v-if="!showInput">
      <p>{{todo.task}}</p>
      <button @click="editTodo">Edit</button>
    </div>
    <ToDoInput v-else @close="closeInput" :editMode="true" :todo="todo" @update-task="updateTask"/>
  </div>
</template>

<script>
import ToDoInput from './ToDoInput.vue';

export default {
  props: ["todo"],

  components: {
    ToDoInput
  },

  data() {
    return {
      showInput: false
    }
  },

  methods: {
    editTodo() {
      this.showInput = true;
    },

    updateTask(todo) {
      this.$emit("update-task", todo)
    },

    closeInput() {
      this.showInput = false;
    }
  }
}
</script>

<style lang="less" scoped>

</style>
