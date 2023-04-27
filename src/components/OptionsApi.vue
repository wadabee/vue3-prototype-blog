<script lang="ts">
import type { TodoType } from '@/@types/Todo'
import OATodoInput from './OATodoInput.vue'
import OATodoList from './OATodoList.vue'

export default {
  name: 'OptionsApi',
  components: {
    OATodoInput,
    OATodoList
  },
  data() {
    return {
      todoList: [] as TodoType[]
    }
  },
  methods: {
    registerTodo(todo: TodoType) {
      this.todoList.push(todo)
    },
    deleteTodo(index: number) {
      this.todoList.splice(index, 1)
    }
  }
}
</script>

<template>
  <div :style="{ display: 'flex', flexDirection: 'column' }">
    <h2>OptionsAPI</h2>
    <OATodoInput @register="registerTodo" />
    <OATodoList :todo-list="todoList" @delete="deleteTodo" />
  </div>
</template>
