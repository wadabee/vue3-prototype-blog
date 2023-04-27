<script lang="ts">
import type { TodoType } from '@/@types/Todo'
import { defineComponent, type PropType } from 'vue'

export default defineComponent({
  name: 'OATodoList',
  props: {
    todoList: {
      type: Object as PropType<TodoType[]>,
      required: true
    }
  },
  emits: {
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    delete: (index: number) => true
  },
  methods: {
    onClickDelete(index: number) {
      this.$emit('delete', index)
    }
  }
})
</script>

<template>
  <h3>Todo List</h3>
  <div v-for="(todo, idx) in todoList" :key="idx">
    <div class="todo">
      <div>
        <h4>{{ todo.title }}</h4>
        <div class="content">
          {{ todo.content }}
        </div>
      </div>
      <button class="delete-button" @click="() => onClickDelete(idx)">Delete</button>
    </div>
  </div>
</template>

<style>
.todo {
  display: flex;
  justify-content: space-between;
  border: solid 1px;
  border-radius: 7px;
  border-color: gray;
  margin: 5px;
}

.content {
  font-size: 0.75rem;
}

.delete-button {
  margin: 5px;
}
</style>
