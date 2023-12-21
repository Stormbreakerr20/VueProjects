<template>
    <div class="flex flex-col gap-3">
        <div class="text-lg font-medium border-b border-gray-300">
        Add new transaction
        </div>
        <form class="flex flex-col gap-2 font-medium" @submit.prevent="onSubmit">
            <div class="flex flex-col gap-1">
                <label for="text">Text</label>
                <input type="text" placeholder="Enter text..." v-model="text" class="bg-white rounded-md p-1" required/>
            </div>
            <div class="flex flex-col gap-1">
                <label for="amount"
                    >Amount <br />
                    (negative - expense, positive - income)</label
                >
                <input type="number" placeholder="Enter amount..." v-model="amt" class="bg-white rounded-md p-1"  required/>
            </div>
            <button class="bg-blue-500 text-white px-4 py-2 rounded-md">
                Add transaction
            </button>
        </form>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';
const props = defineProps({
    transactions: Array,
})

import { ref } from 'vue';
const text = ref('');
const amt = ref();

const onSubmit = () => {
    const transaction = {
        id: Math.floor(Math.random() *10000),
        method: text.value,
        amt: amt.value
    }
    props.transactions.push(transaction);
    text.value = '';
    amt.value = null;
    localStorage.setItem('transactions', JSON.stringify(props.transactions));
}

</script>