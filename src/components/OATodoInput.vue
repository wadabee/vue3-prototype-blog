<script lang="ts">
import type { TodoType } from '@/@types/Todo'
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'OATodoInput',
  data() {
    return {
      title: '',
      content: ''
    }
  },
  emits: {
    // eslint-disable-next-line @typescript-eslint/no-unused-vars
    register: (_todo: TodoType) => true
  },
  methods: {
    onClickRegister() {
      this.$emit('register', {
        title: this.title,
        content: this.content
      })
    }
  }
})
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
