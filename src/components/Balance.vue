<template>
    <div style="margin: 10px 0;">
        <h4 style="font-weight: bold;">YOUR BALANCE</h4>
        <h2>{{ formattedTotal }}</h2>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';

// Reactive total balance
const total = ref(0.00);

// Computed property to format the total balance
const formattedTotal = computed(() => {
    return total.value.toLocaleString('en-US', { style: 'currency', currency: 'USD' });
});
</script>

<style scoped>
*{
    margin: 0;
    padding: 0;
}
h4 {
    font-weight: 500;
}
</style>
