<template>
    <div class="fluctuation-container">
        <div class="income-tag section">
            <h4 class="title">Income</h4>
            <h4 id="income">+{{ totalIncomeUS }}</h4>
        </div>
        <div class="expense-tag section">
            <h4 class="title">Expenses</h4>
            <h4 id="expenses">-{{ totalExpensesUS }}</h4>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';

// Reactive state for income and expenses
const totalIncome = ref(0);
const totalIncomeUS = computed(() => totalIncome.value.toLocaleString('en-US', { style: 'currency', currency: 'USD' }));

const totalExpenses = ref(0);
const totalExpensesUS = computed(() => totalExpenses.value.toLocaleString('en-US', { style: 'currency', currency: 'USD' }));
</script>

<style scoped>
.fluctuation-container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 20px;
}
.section {
    background-color: #fff;
    padding: 16px 40px;
}
.section .title{
    font-weight: bold;
    font-size: 1.2rem;
}
#income {
    color: green;
}

#expenses {
    color: red;
}
</style>
