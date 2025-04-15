<script setup>
import { faker } from '@faker-js/faker'
//change these
// const firstname = faker.person.firstName()
// const lastname = faker.person.lastName()
// const jobtitle = faker.person.jobTitle()
// const email = faker.internet.email()
// const phone = faker.phone.number()
// const bio = faker.lorem.lines(2)
// const username = faker.internet.userName({ firstName: firstname, lastName: lastname, email: email, number: phone }).toLowerCase()
//const userinfo = faker.internet.userInfo({email: email, number: phone}).toLowerCase()

const props = defineProps({
    employee: {
        type: Object,
        required: true,
        default: () => {
            return {
                _id: "67f5846c5f310e9932134d6b",
                userName: "jperez",
                firstName: "Joseph",
                lastName: "Perez",
                title: "Computer Science Wizard",
                quote: "You shall not pass!!",
                __v: 0,
            }
        },
    },
})
</script>

<template>
    <!--Tell router link where to link to-->
    <!--This lets you click the card as a link for card details-->
    <RouterLink :to="{ name: 'CardDetail', params: { id: props.employee._id }}">
        <!--Use tailwind for CSS options-->
        <div class="border border-gray-500 rounded-lg shadow bg-gray-400 h-full">
            <!--Change image to something else-->
            <img class="object-fill h-48000px w-96000px rounded-t-lg" v-bind:src="faker.image.urlLoremFlickr({category:'people', height: 48000000, width: 96000000})" />
            <div class="p-4">
                <p class="mb-2 text-2xl font-bold">{{ props.employee.firstName }} {{ props.employee.lastname }}</p>
                <p class="mb-3 font-normal text-gray-800">Job Title: {{ props.employee.title}}</p>
                <p class="mb-3 font-normal text-gray-800">Email: {{ props.employee.quote }}</p>
            </div>
        </div>
    </RouterLink>
    <!--{{ firstname }} {{ lastname }} <br/> -->
</template>