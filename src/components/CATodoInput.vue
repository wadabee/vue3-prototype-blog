<script setup lang="ts">
import type { TodoType } from '@/@types/Todo'
import { defineComponent, ref } from 'vue'

defineComponent({
  name: 'CATodoInput'
})

const title = ref<string>('')
const content = ref<string>('')

const emits = defineEmits<{
  (e: 'register', newTodo: TodoType): void
}>()

const onClickRegister = () => {
  emits('register', {
    title: title.value,
    content: content.value
  })
}
</script>

<template>
  <h3>New ToDo</h3>
  <div class="input-field">
    <label for="title">Title</label>
    <input
      type="text"
      id="title"
      :value="title"
      @input="
        (e :any) => {
          title = e.target.value
        }
      "
    />
  </div>

  <div class="input-field">
    <label for="content">Content</label>
    <input
      type="text"
      id="content"
      :value="content"
      @input="
        (e :any) => {
          content = e.target.value
        }
      "
    />
  </div>
  <button @click="onClickRegister">Register</button>
</template>

<style>
.input-field {
  display: flex;
  justify-content: space-between;
  margin-bottom: 5px;
}
</style>
