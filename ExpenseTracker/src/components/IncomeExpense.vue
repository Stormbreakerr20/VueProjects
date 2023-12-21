<template>
  <div class="bg-white shadow-md flex min-w-[350px] justify-between p-3 rounded-md border-black ">
    <div class="flex-grow bg-white flex justify-center flex-col items-center font-medium border-r border-black ">
      INCOME
      <p id="money-plus" class="money plus text-green-600 bg-white">+${{income}}</p>
    </div>
    <div class="flex-grow bg-white flex font-medium justify-center flex-col items-center">
      EXPENSE
      <p id="money-minus" class="money minus text-red-500 font-medium bg-white">${{expense}}</p>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
const props = defineProps({
    income: Number,
    expense: Number
})
</script>