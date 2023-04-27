<script setup lang="ts">
import type { TodoType } from '@/@types/Todo'
import { defineComponent } from 'vue'

defineComponent({
  name: 'CAWithoutEmitsTodoList'
})

const props = defineProps<{
  todoList: TodoType[]
  onDelete: (index: number) => void
}>()

const onClickDelete = (index: number) => {
  props.onDelete(index)
}
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
