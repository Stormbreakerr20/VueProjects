<template>
    <div class="">
        Your Balance
        <div class="text-3xl font-medium" id="balance">${{ total }}</div>
    </div>
</template>


<script setup>
import { defineProps } from 'vue';
const props = defineProps({
    total: Number
})
</script>