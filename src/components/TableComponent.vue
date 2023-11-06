<script setup lang="ts">
import axios from 'axios'
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

const rows = ref([
  {
    id: 1,
    name: 'Apple MacBook Pro 17"',
    color: 'Grey',
    category: 'Laptop',
    price: '$5000'
  },
  {
    id: 2,
    name: 'Samsung TV',
    color: 'Black',
    category: 'TV',
    price: '$800'
  }
])

const search = ref('')

function ScrapeData(e: Event) {
  e.preventDefault()
  let config = {
    method: 'get',
    maxBodyLength: Infinity,
    url: `http://localhost:3005?search=${search.value}`,
    headers: {}
  }

  axios
    .request(config)
    .then((response) => {
      console.log(response.data)
    })
    .catch((error) => {
      console.log(error)
    })
}

</script>

<template>
  <div class="m-5 md:mx-20 mt-10 font-sans">
    <div class="flex flex-col justify-center items-center">
      <h1 class="text-5xl font-bold mb-4">Goggle Maps Scrapper</h1>
      <p>Get data out of google maps easily</p>
    </div>
    <div class="my-12 mx-0">
      <form class="flex flex-col justify-center md:flex-row mx-0 md:mx-20 space-y-4 md:space-y-0 space-x-0 md:space-x-4">
        <input v-model="search" placeholder="Goggle maps search"
          class="w-full md:w-8/12 border-2 px-5 py-2 border-gray-500 rounded-sm" type="text" name="search" id="search" />
        <button @click="ScrapeData" class="whitespace-nowrap px-10 py-2 text-white bg-blue-600">Search</button>
      </form>
    </div>
    <div class="relative overflow-x-auto border sm:rounded-lg">
      <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
        <thead class="text-xs text-gray-700 uppercase bg-sky-50 dark:text-gray-400">
          <tr>
            <th v-for="column in columns" :key="column.id" scope="col" class="px-6 py-3">
              {{ column.name }}
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="row in rows" :key="row.id"
            class="bg-white border-b dark:bg-gray-800 dark:border-blue-700 hover:bg-gray-50 dark:hover:bg-gray-600">
            <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
              {{ row.name }}
            </th>
            <td class="px-6 py-4">{{ row.color }}</td>
            <td class="px-6 py-4">{{ row.category }}</td>
            <td class="px-6 py-4">{{ row.price }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
