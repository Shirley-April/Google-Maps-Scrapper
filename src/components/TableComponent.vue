<script setup lang="ts">
import { ref } from 'vue'

interface Columns {
  name: string
  color: string
  category: string
  price: number
}

const columns = ref([
  { id: 1, name: 'Product name' },
  { id: 2, name: 'Color' },
  { id: 3, name: 'Category' },
  { id: 4, name: 'Price' }
])

const search = ref('')

</script>

<template>
  <div class="m-5 md:mx-20 mt-10   font-sans">
    <div class="flex flex-col justify-center items-center">
      <h1 class="text-5xl font-bold mb-4">Goggle Maps Scrapper</h1>
      <p>Get data out of google maps easily</p>
    </div>
    <div class="my-12 mx-0">
      <form class="flex flex-col justify-center	 md:flex-row mx-0 md:mx-20 space-y-4 md:space-y-0 space-x-0 md:space-x-4">
        <input v-model="search" placeholder="Goggle maps search"
          class="w-full md:w-8/12 border-2 px-5 py-2 border-gray-500 rounded-sm" type="text" name="search" id="search">
        <button class="whitespace-nowrap	 px-10 py-2 text-white bg-blue-600	">Search</button>
      </form>
    </div>
    <div class="relative overflow-x-auto border sm:rounded-lg">
      <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
        <thead class="text-xs text-gray-700 uppercase bg-sky-50	 dark:text-gray-400">
          <tr>
            <th v-for="column in columns" :key="column.id" scope="col" class="px-6 py-3">
              {{ column.name }}
            </th>
          </tr>
        </thead>
        <tbody>
          <tr class="bg-white border-b dark:bg-gray-800 dark:border-blue-700 hover:bg-gray-50 dark:hover:bg-gray-600">
            <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
              Apple MacBook Pro 17"
            </th>
            <td class="px-6 py-4">Silver</td>
            <td class="px-6 py-4">Laptop</td>
            <td class="px-6 py-4">$2999</td>
            <!-- <td class="px-6 py-4 text-right">
            <a href="#" class="font-medium text-blue-600 dark:text-blue-500 hover:underline">Edit</a>
          </td> -->
          </tr>
          <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-600">
            <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
              Microsoft Surface Pro
            </th>
            <td class="px-6 py-4">White</td>
            <td class="px-6 py-4">Laptop PC</td>
            <td class="px-6 py-4">$1999</td>
            <!-- <td class="px-6 py-4 text-right">
            <a href="#" class="font-medium text-blue-600 dark:text-blue-500 hover:underline">Edit</a>
          </td> -->
          </tr>
          <tr class="bg-white dark:bg-gray-800 hover:bg-gray-50 dark:hover:bg-gray-600">
            <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
              Magic Mouse 2
            </th>
            <td class="px-6 py-4">Black</td>
            <td class="px-6 py-4">Accessories</td>
            <td class="px-6 py-4">$99</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
