<script setup>
import { defineProps, inject } from 'vue';

const props = defineProps({
  client: Object,
});

const darkTheme = inject('darkTheme');
</script>

<template>
    <div :class="{ ' text-black': !darkTheme, ' text-white': darkTheme }"  class="text-right">
        <div class="p-3 m-3 rounded-lg" :class="{ ' bg-gray-50': !darkTheme, ' bg-gray-700': darkTheme }">

            <h1><b :class="{ 'bg-gray-50': !darkTheme, 'bg-gray-500': darkTheme }" class="rounded-lg p-2">Name:</b>  {{ client.first_name }} {{ client.last_name }}</h1> <br>
            <h1><b :class="{ 'bg-gray-50': !darkTheme, 'bg-gray-500': darkTheme }" class="rounded-lg p-2">Address:</b>  {{ client.address }}</h1> <br>
            <h1><b :class="{ 'bg-gray-50': !darkTheme, 'bg-gray-500': darkTheme }" class="rounded-lg p-2">Phone:</b>  {{ client.phone }}</h1> <br>
            <h1><b :class="{ 'bg-gray-50': !darkTheme, 'bg-gray-500': darkTheme }" class="rounded-lg p-2">Credit Limit: </b> {{ client.credit_limit }}</h1>
        </div>
    </div>
  </template>
