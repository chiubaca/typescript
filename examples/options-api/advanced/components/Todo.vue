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
import Vue, { PropType } from 'vue'
import { Task } from '../types'

export default Vue.extend({
  name: 'Todo',
  props: {
    task: {
      type: Object as PropType<Task>,
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
