<script setup lang="ts">
import { defineComponent, ref } from 'vue'
import CAWithoutEmitsTodoInput from './CAWithoutEmitsTodoInput.vue'
import type { TodoType } from '@/@types/Todo'
import CAWithoutEmitsTodoList from './CAWithoutEmitsTodoList.vue'

defineComponent({
  name: 'CompositionApiWithoutEmits'
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
    <h2>Composition API w/o Emits</h2>
    <CAWithoutEmitsTodoInput :on-register="registerTodo" />
    <CAWithoutEmitsTodoList :todo-list="todoList" :on-delete="deleteTodo" />
  </div>
</template>
