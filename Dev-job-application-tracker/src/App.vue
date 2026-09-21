<script setup>
import { ref, onMounted } from 'vue'
import JobCard from './components/JobCard.vue';


const searchInput = ref(null)
const jobs = ref([
  {
    id: 1,
    company: 'DevelopCatsDogs',
    position: 'Frontend Developer (Vue 3)',
    salary: '4,000',
    status: 'Интервью'
  },
  {
    id: 2,
    company: 'Freelance Client',
    position: 'Fullstack Python / Vue',
    salary: '35/час',
    status: 'Отправлено'
  },
  {
    id: 3,
    company: 'New Tech Startup',
    position: 'Junior Vue Developer',
    salary: '1,500',
    status: 'Оффер'
  }
])
const removeJob = (id) => {
  jobs.value = jobs.value.filter((j) => j.id != id)
}
onMounted(() => searchInput.value.focus())
</script>

<template>
  <main class="container">
    <h1><span>&#x1F4BC;</span> Dev Job Tracker</h1>
<input ref="searchInput" type="text" placeholder="Поиск вакансий..." />
    <div class="jobs-list">
      <JobCard v-for="job in jobs" :key="job.id" :job="job" @delete="removeJob"/>
    </div>
  </main>
</template>

<style scoped>
* {
  font-family: Impact, 'Arial Narrow Bold', sans-serif;
}
.container {
  max-width: 600px;
  margin: 30px auto;
  font-family: sans-serif;
}
.jobs-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
</style>
