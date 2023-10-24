<script setup>
import { computed, defineProps, inject } from 'vue';

const props = defineProps({
  client: Object,
  sales: Array,
});

const totalAmount = computed(() => {
  return props.sales.reduce((sum, obj) => sum + (obj.amount || 0), 0);
});

const darkTheme = inject('darkTheme');
</script>


<template>
    <div :class="{ 'filter invert': darkTheme }" class="">
      <div class="overflow-hidden shadow-sm sm:rounded-lg p-8">
        <h3 :class="{ 'text-gray-700': !darkTheme, 'text-black': darkTheme }" class="mb-2 text-xl font-semibold text-gray-700 dark:text-dark">Sales Transactions</h3>
        <table class="w-full border-collapse">
          <thead>
            <tr :class="{ 'text-s-700': !darkTheme, 'text-black': darkTheme }"    class="bg-gray-100 dark:bg-red-900 dark:text-white">
              <th class="px-4 py-2 text-left">Date</th>
              <th class="px-4 py-2 text-left">Cash/Credit</th>
              <th class="px-4 py-2 text-left">Total</th>
            </tr>
          </thead>
          <tbody>
            <tr :class="{ 'text-gray-700': !darkTheme, 'text-black': darkTheme }" v-for="sale in sales" :key="sale.id" class="border-b border-gray-900 dark:border-gray-900">
              <td :class="{ 'text-gray-700': !darkTheme, 'text-black': darkTheme }" class="px-4 py-2 dark:text-dark">{{ sale.date }}</td>
              <td :class="{ 'text-gray-700': !darkTheme, 'text-black': darkTheme }" class="px-4 py-2 dark:text-dark">{{ sale.is_credit ? 'Credit' : 'Cash' }}</td>
              <td :class="{ 'text-gray-700': !darkTheme, 'text-black': darkTheme }" class="px-4 py-2 dark:text-dark">{{ sale.amount }}</td>
            </tr>
            <tr>
              <td colspan="2" style="font-size: 50px;" class="px-4 py-2 font-semibold text-right dark:text-dark">Sum:</td>
              <td class="px-4 py-2 text-xl font-semibold text-center dark:text-dark">{{ totalAmount }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </template>
