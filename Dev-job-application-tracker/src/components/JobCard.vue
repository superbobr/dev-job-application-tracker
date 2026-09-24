<script setup>
import StatusBadge from './StatusBadge.vue'
import { ref, computed } from 'vue'
const props = defineProps({job: Object})
const emit = defineEmits(['delete'])
const deleteJob = () => {
    emit('delete', props.job.id)
}
const borderColor = computed(() => {
  switch (props.job.status) {
    case 'Оффер':
      return '#22c55e'
    case 'Интервью':
      return '#3b82f6'
    case 'Отправлено':
      return '#eab308'
    default:
      return '#9ca3af'
  }
})
</script>
<template>
    <div class="job-card">
<p>Компания: {{ job.company }}</p>
<p>Должность: {{ job.position }}</p>
<p>Зарплата: {{ job.salary }}</p>
<p>Статус: <StatusBadge>
     {{ job.status }}
  </StatusBadge></p>
<button @click="deleteJob">Удалить</button>
</div>
</template>
<style scoped>
.job-card {
  border: 2px solid v-bind(borderColor);
  border-radius: 8px;
  padding: 12px;
  transition: border-color 0.3s ease;
}

button {
  background-color: #ef4444;
  color: white;
  border: none;
  padding: 6px 12px;
  border-radius: 4px;
  cursor: pointer;
}
</style>