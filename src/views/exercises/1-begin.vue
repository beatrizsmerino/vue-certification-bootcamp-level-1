<script setup lang="ts">
import { ref } from "vue";
const name = ref("Bootcampers");
const item = ref("coffee");
</script>
<template>
  <div class="viewport-center">
    <div>
      <label for="name">Name:</label>
      <input type="text" name="name" id="name" v-model="name">
      <br/>
      <label for="item">Item:</label>
      <input type="text" name="item" id="item" v-model="item">
      <hr/>
      <p>
        Hello {{ name }}! Do you like {{ item }}?
      </p>
    </div>
  </div>
</template>
