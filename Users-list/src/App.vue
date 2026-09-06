<script setup>
import { ref, computed } from 'vue'
import UserCard from './components/UserCard.vue';
const users = ref([
  { id: 1, name: 'Леон', age: 44 },
  { id: 2, name: 'Алекс', age: 30 },
  { id: 3, name: 'Иван', age: 25 }
])
const userName = ref('')
const userAge = ref(0)
const addUser = () => {
  userName.value = userName.value.trim()
  if(!userName.value) {
    return
  }
  if(userAge.value && userAge.value >= 1) {
    const lastUser = users.value.at(-1)
    const newId = lastUser ? lastUser.id + 1 : 1
    users.value.push({
      id: newId,
      name: userName.value,
      age: userAge.value
    })
    userName.value = ''
    userAge.value = ''
  } else {
    return
  }
}
const delUser = (id) => users.value = users.value.filter(user => user.id != id)
const usersCount = computed(() => users.value.length)
</script>

<template>
  <h1>Список пользователей</h1>
  <div class="add-user">
    <h2>Добавить пользователя</h2>
    <input type="text" placeholder="Имя" v-model="userName">
    <input type="text" placeholder="Возраст" v-model="userAge">
    <p>Всего пользователей: {{usersCount}}</p>
    <button @click="addUser">Добавить пользователя</button>
  </div>
  <div class="users-list">
  <UserCard v-for="user in users" :key="user.id" :user="user" @delete="delUser"/>
  </div>
</template>

<style scoped>
* {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
.add-user {
  margin-bottom: 10px;
}
.add-user input {
  margin-right: 10px;
}
.user-card {
  width: 30%;
  border: 2px solid green;
  padding: 5px;
  margin-bottom: 10px;
}
</style>
