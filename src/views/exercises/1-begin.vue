<script setup lang="ts">
import { ref } from "vue";
const name = ref("Bootcampers");
const item = ref("coffee");
</script>
<template>
  <div class="viewport-center">
    <div>
      <div class="mb-4">
        <label for="name" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">
          Name:
        </label>
        <input type="text" name="name" id="name" v-model="name" placeholder="Enter your name" required
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
      </div>
      <div>
        <label for="item" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">
          Item:
        </label>
        <input type="text" name="item" id="item" v-model="item" placeholder="Enter an item" required
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
      </div>
      <div
        class="block w-full mt-8 p-6 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
        <p>
          Hello {{ name }}! Do you like {{ item }}?
        </p>
      </div>
    </div>
  </div>
</template>
