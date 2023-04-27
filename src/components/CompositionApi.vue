<script setup lang="ts">
import { defineComponent, ref } from 'vue'
import CATodoInput from './CATodoInput.vue'
import type { TodoType } from '@/@types/Todo'
import CATodoList from './CATodoList.vue'

defineComponent({
  name: 'CompositionApi'
})

const todoList = ref<TodoType[]>([])
const registerTodo = (todo: TodoType) => {
  todoList.value.push(todo)
}

const deleteTodo = (index: number) => {
  todoList.value.splice(index, 1)
}
</script>

<template>
  <div :style="{ display: 'flex', flexDirection: 'column' }">
    <h2>Composition API</h2>
    <CATodoInput @register="registerTodo" />
    <CATodoList :todo-list="todoList" @delete="deleteTodo" />
  </div>
</template>
