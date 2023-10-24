<script setup>
import { defineProps, inject } from 'vue';

const props = defineProps({
    sales: Array, // Ensure that this type matches the type of your sales prop
});

const darkTheme = inject('darkTheme');
</script>

<template>
    <div :class="darkTheme ? 'text-white' : 'text-gray-700'" class="h-[150px] w-[1000px] m-10 p-3 shadow-sm rounded-lg" v-for="sale in sales" :key="sale.id">
        <h1><b :class="{ 'bg-gray-50': !darkTheme, 'bg-gray-500': darkTheme }" class="rounded-lg p-2">Client ID:</b> {{ sale.id }}</h1> <br>
        <h1><b :class="{ 'bg-gray-50': !darkTheme, 'bg-gray-500': darkTheme }" class="rounded-lg p-2">Date:</b> {{ sale.date }}</h1> <br>
        <h1><b :class="{ 'bg-gray-50': !darkTheme, 'bg-gray-500': darkTheme }" class="rounded-lg p-2">Is Credited:</b> {{ sale.is_credit ? 'Yes' : 'No'  }}</h1>
    </div>


    <!-- <div :class="darkTheme ? 'text-white' : 'text-gray-700'" class="mx-auto max-w-7xl sm:px-6 lg:px-8">
      <div :class="darkTheme ? 'bg-black' : 'bg-white'" class="overflow-hidden shadow-sm sm:rounded-lg">
        <div :class="darkTheme ? 'text-white' : 'text-gray-700'" class="p-6 text-gray-900">

          <table class="min-w-full divide-y divide-gray-200">
            <thead>
              <tr>
                <th class="px-6 py-3 text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase bg-gray-50 dark:bg-gray-800 dark:text-gray-400">
                  Date
                </th>
                <th class="px-6 py-3 text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase bg-gray-50 dark:bg-gray-800 dark:text-gray-400">
                  Client ID
                </th>
                <th class="px-6 py-3 text-xs font-medium leading-4 tracking-wider text-left text-gray-500 uppercase bg-gray-50 dark:bg-gray-800 dark:text-gray-400">
                  Is Credit
                </th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="sale in sales" :key="sale.id">
                <td class="px-6 py-4 whitespace-no-wrap">
                  {{ sale.date }}
                </td>
                <td class="px-6 py-4 whitespace-no-wrap">
                  {{ sale.client_id }}
                </td>
                <td class="px-6 py-4 whitespace-no-wrap">
                  {{ sale.is_credit ? 'Yes' : 'No' }}
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div> -->
  </template>
