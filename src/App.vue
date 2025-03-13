<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import Fluctuation from "./components/Fluctuation.vue";
import History from "./components/History.vue";
import AddTransaction from "./components/AddTransaction.vue";

import { reactive, computed } from "vue";
import { useToast } from 'vue-toastification';

const Transactions = reactive([
    { id: 1, name: 'Item 1', cost: 2100 },
    { id: 2, name: 'Item 2', cost: -200 },
    { id: 3, name: 'Item 3', cost: 300 }
]);

const toast = useToast();

const incomeCost = computed(() => {
    return Transactions.reduce((acc, transaction) => acc + (transaction.cost > 0 ? transaction.cost : 0), 0);
});

const expensesCost = computed(() => {
    return Transactions.reduce((acc, transaction) => acc + (transaction.cost < 0 ? Math.abs(transaction.cost) : 0), 0);
});

const total = computed(() => {
    return incomeCost.value - expensesCost.value;
});

function handleTransactionSubmitted(item) {
    Transactions.push({
        id: generateUniqueId(),
        name: item.name,
        cost: item.cost,
    });
    toast.success('Thêm thành công');
}

function generateUniqueId() {
    return Transactions.length + 1;
}

// Delete
function handleTransactionDeleted(id) {
    const index = Transactions.findIndex(transaction => transaction.id === id);
    if (index !== -1) {
        Transactions.splice(index, 1); // Sử dụng splice để xóa mục khỏi mảng
        toast.success('Xóa thành công');
    }
}
</script>

<template>
  <header>
    <Header />
  </header>

  <main>
    <Balance :total="total" />
    <Fluctuation :totalIncome="incomeCost" :totalExpenses="expensesCost" />
    <History :history="Transactions" @deleted="handleTransactionDeleted"/>
    <AddTransaction @transactionSubmitted="handleTransactionSubmitted" />
  </main>
</template>

<style scoped>
</style>
