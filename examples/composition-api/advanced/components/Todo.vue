<template>
  <li class="to-do">
    <span :class="{complete: task.complete}">{{ task.name }}</span>
    <button @click="$emit('complete', index)">
      ✅
    </button>
    <button @click="$emit('delete', index)">
      🗑️
    </button>
  </li>
</template>

<script lang="ts">
import { defineComponent } from '@vue/composition-api'
import { Task } from '../types'

export default defineComponent({
  name: 'Todo',
  props: {
    task: {
      type: Object as () => Task,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  }
})
</script>

<style >
.complete{
  text-decoration: line-through
}
</style>
