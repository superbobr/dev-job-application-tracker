<script setup>
import { ref } from 'vue'
const props = defineProps(['user']) 
const emit = defineEmits(['delete'])
const onDelete = () => {
    emit('delete', props.user.id)
}
</script>
<template>
<div class="user-card">
    <p>Имя: {{user.name}}</p>
    <p>Возраст: {{user.age}}</p>
    <button @click="onDelete">Удалить</button>
    </div>
</template>
<style scoped>

</style>