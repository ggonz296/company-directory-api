<script setup>
import {ref, onMounted, onUnmounted} from 'vue'
import { useRoute } from 'vue-router'
import useAPI from '@/composables/useAPI'
import { faker } from '@faker-js/faker'

const{fetchEmployee, currentEmployee} = useAPI()

onMounted(async () => {
    await fetchEmployee(route.params.id)
})

onUnmounted(() => {
    currentEmployee.value = null
})
const route = useRoute()
</script>

<template>
    <!--When user clicks on card link, it will display this-->
    <!--Could potentially send in other user information--
    <div class="text-center">
        <h1 class="font-bold">{{route.params.id}}</h1>
        <p class="text-lg">Job Title: {{ route.query.jobtitle }}</p>
        <p class="mb-3 font-normal text-gray-800">Email: {{ route.query.email }}</p>
        <p class="mb-3 font-normal text-gray-800">Phone: {{ route.query.phone }}</p>
        <p class="mb-3 font-normal text-gray-800">Bio: {{ route.query.bio }}</p>
    
    </div>-->

    <main>
        <div v-if="currentEmployee" class="flex flex-col items-center justify-center gap-6">
            <h1 class="text-6xl font-bold p-5">{{ currentEmployee.firstName }}{{ currentEmployee.firstName }}</h1>
            <h1 class="text-3xl p-5">{{ currentEmployee.title }}</h1>
            <h1 class="text-3xl p-5">{{ currentEmployee.userName }} @southtexascollege.edu</h1>
            <h1 class="text-3xl p-5">{{ currentEmployee.quote }}</h1>

            <img class="p-8" :src="faker.image.urlLoremFlickr({category:'cat'})">
        </div>
    </main>
</template>