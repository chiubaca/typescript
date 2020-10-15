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
import { Vue, Component, Prop } from 'vue-property-decorator'
import { Task } from '../types'

@Component
export default class Todo extends Vue {
@Prop() readonly task!: Task;
@Prop() readonly index!: Number;
}
</script>

<style >
.complete{
  text-decoration: line-through
}
</style>
