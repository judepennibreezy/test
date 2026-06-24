<script setup></script>

<template>
<div class='container py-3'>

<div class='px-4 py-5 my-5 text-center text-white'>
    Penny nuts shop
</div>
   <!-- Bind input to the search query -->
    <input  class='form-control'
      type="text" 
      v-model="searchQuery" 
      placeholder="Search items by name..." 
    />

  <ul class="list-group bg-secondary">
      <!-- Loop through the imported JSON data -->
      <li v-for="item in filteredItems" :key="item.id" class='list-group-item bg-secondary'>
           <img :src="item.iconUrl" alt="Small Image" class="rounded-circle me-3 ">
  {{ item.name }} - {{ item.buyerPrice }}
      </li>
    </ul>

    </div>
</template>

<style scoped></style>
<script setup>


import { ref, computed } from 'vue';
import myData from './price.json'

// 2. Bind it to a variable (it is available to the template automatically)
const products = myData;

// 1. Reactive reference for the search text
const searchQuery = ref('');

// 2. Original dataset
const items = myData;

// 3. Dynamic search logic
const filteredItems = computed(() => {
 
  return items.filter(item => {
    return item.name.toLowerCase().includes(searchQuery.value.toLowerCase());
  });
});
</script>
