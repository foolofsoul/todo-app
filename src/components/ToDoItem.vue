<template>
  <div class="todo__item">
    <div v-if="!showInput" class="todo__item-info">
      <input type="checkbox" v-model="todoComplete">
      <p>{{todo.task}} <span class="todo__item-line" :style="{transform: `scaleX(${todoComplete ? '1' : '0'})`}"></span></p>
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
      showInput: false,
      todoComplete: false
    }
  },

  methods: {
    editTodo() {
      this.showInput = true;
    },

    updateTask(todo) {
      this.$emit("update-task", todo);
    },

    closeInput() {
      this.showInput = false;
    }
  }
}
</script>

<style lang="less" scoped>
.todo__item {
  margin-bottom: 12px;

  &-info {
    display: flex;
    align-items: center;

    p {
      position: relative;
      margin-right: 16px;
      margin-left: 8px;
    }
  }

  &-line {
    position: absolute;
    top: 50%;
    display: inline-block;
    height: 2px;
    width: 100%;
    background-color: #333;
    transform-origin: left;
    transition: transform .1s ease-in-out;
  }
}
</style>
