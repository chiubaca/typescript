<template>
  <div class="to-do-container">
    <h1>To Do's</h1>
    <div>
      <input
        v-model="task"
        type="text"
        placeholder="What to do?"
        @keyup.enter="addTodo"
      >
      <button @click="addTodo">
        Add Todo
      </button>
      <ul v-for="(item, index) in allTasks" :key="index">
        <Todo :task="item" :index="index" @delete="handleDelete" @complete="handleComplete" />
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Todo from '../components/Todo.vue'
import { Task } from '../types'

export default Vue.extend({
  name: 'OptionsAPITodo',
  components: {
    Todo
  },
  data (): { task: string; allTasks: Task[] } {
    return {
      task: '',
      allTasks: []
    }
  },
  methods: {
    addTodo () {
      this.allTasks.push({
        name: this.task,
        complete: false
      })
      this.task = ''
    },
    handleDelete (index: number) {
      this.allTasks.splice(index, 1)
    },
    handleComplete (index: number) {
      this.allTasks[index].complete = true
    }
  }
})
</script>

<style>
h1 {
text-decoration: underline;
}
.to-do-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 2rem;
}
</style>
