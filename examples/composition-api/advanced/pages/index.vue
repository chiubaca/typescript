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
        <Todo
          :task="item"
          :index="index"
          @delete="handleDelete"
          @complete="handleComplete"
        />
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from '@vue/composition-api'
import Todo from '../components/Todo.vue'
import { Task } from '../types'

export default defineComponent({
  components: {
    Todo
  },
  setup () {
    const task = ref('')
    const allTasks = ref<Task[]>([])

    function addTodo () {
      allTasks.value.push({
        name: task.value,
        complete: false
      })
      task.value = ''
    }

    function handleDelete (index: number) {
      allTasks.value.splice(index, 1)
    }

    function handleComplete (index: number) {
      allTasks.value[index].complete = true
    }

    return {
      task,
      allTasks,
      addTodo,
      handleDelete,
      handleComplete
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