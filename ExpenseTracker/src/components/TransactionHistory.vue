<template>
    <div class="flex flex-col gap-2">
        <div class="text-lg font-medium border-b border-gray-300">
            History
        </div>
        <ul class="flex flex-col gap-2  max-h-[18vh] overflow-y-scroll relative pr-2"> 
                <li id="li" v-for="transaction in transactions" :key="transaction.id" class=" bg-white cursor-pointer shadow-md transition-all duration-200 flex justify-between p-2 rounded-md" :class = "transaction.amt >= 0 ? 'plus' : 'minus'">
                    <div id="cross" class="bg-red-500 p-1 px-[6px] text-xs cursor-pointer rounded-sm absolute left-0 transition-all duration-100" @click="handleClick">x</div>
                    <span class="bg-white">{{transaction.method}}</span>
                    <span class="bg-white">${{transaction.amt}}</span>
                </li>
        </ul>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    transactions: Array,
})

const handleClick = (e) => {
    const id = e.target.parentElement.id;
    const index = props.transactions.findIndex(transaction => transaction.id == id);
    props.transactions.splice(index, 1);
    localStorage.setItem('transactions', JSON.stringify(props.transactions));
}
</script>

<style scoped>
.plus:hover{
    border-right: 4px solid #26C367;
}
.minus:hover{
    border-right: 4px solid #B73225;
}
#cross{
    opacity: 0;
}
#li:hover #cross{
    opacity: 1;
}
#li:hover{
    margin-left: 1.4rem;
}

</style>