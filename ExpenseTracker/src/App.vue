<template>
    <div class="flex flex-col gap-2 text-sm h-[100svh] justify-center items-center">
        <header>
            <Header />
        </header>
        <div class="flex flex-col gap-3">
            <Balance :total = "total"/>
            <IncomeExpense :income = "income" :expense = "expense" />
            <TransactionHistory :transactions = "transactions"/>
            <AddTransaction  :transactions = "transactions"/>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import Header from './components/Header.vue';
import Balance from './components/Balance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransactionHistory from './components/TransactionHistory.vue';
import AddTransaction from './components/AddTransaction.vue';

import { onMounted } from 'vue';

onMounted(() => {
    const data = JSON.parse(localStorage.getItem('transactions'));
    console.log(data);
    if(data){
        transactions.value = data;
    }
})

const transactions = ref([])

import { computed } from 'vue';
const total = computed(() => {
    return transactions.value.reduce((acc, curr) => acc + curr.amt, 0)
})
const expense = computed(() => {
    return transactions.value.filter(transaction => transaction.amt < 0).reduce((acc, curr) => acc + curr.amt, 0)
})
const income = computed(() => {
    return transactions.value.filter(transaction => transaction.amt > 0).reduce((acc, curr) => acc + curr.amt, 0)
})

</script>
