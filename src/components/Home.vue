<script setup>
import { ref, onMounted } from 'vue'
import { useAuthStore } from '../stores/auth'
// import axios from 'axios'

// const user = ref()

// const getToken = async () => {
//     await axios.get('/sanctum/csrf-cookie')
// }

//pinia atang a tih dan tur
const authStore = useAuthStore()

onMounted(async () => {
    await authStore.getUser()
    //get Token
    // await getToken()
    //get User
    // const data = await axios.get('/api/user');
    // user.value = data.data
    // console.log(user.value)
})
</script>
<template>
    <div v-if="authStore.user">
        <h1>{{ authStore?.user?.name }}</h1>
        <p>{{ authStore?.user?.email }}</p>
    </div>
    <div v-else>
        <h1>Login to show item</h1>
    </div>
</template>