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
import { computed, defineProps } from 'vue';

// Define the props for income and expenses
const props = defineProps({
    totalExpenses: {
        type: Number,
        required: true
    },
    totalIncome: {
        type: Number,
        required: true
    }
});

const totalIncomeUS = computed(() => 
    props.totalIncome.toLocaleString('en-US', { style: 'currency', currency: 'USD' })
);

const totalExpensesUS = computed(() => 
    props.totalExpenses.toLocaleString('en-US', { style: 'currency', currency: 'USD' })
);
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
.section .title {
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
