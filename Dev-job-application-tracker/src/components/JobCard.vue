<script setup>
import StatusBadge from './StatusBadge.vue'
const props = defineProps({job: Object})
const emit = defineEmits(['delete'])
const deleteJob = () => {
    emit('delete', props.job.id)
}
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
    border-top: 4px solid;
}
</style>