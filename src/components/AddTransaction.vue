<template>
    <div>
        <h2>Add New Transaction</h2>
        <hr>
        <form @submit.prevent="onSubmit">
            <div class="section">
                <h3>Text</h3>
                <input type="text" id="name" v-model="name" placeholder="Enter text ...">
            </div>
            <div class="section">
                <h3>Amount</h3>
                <input type="number" id="amount" v-model="amount" placeholder="Enter amount ...">
            </div>
            <button type="submit">Add Transaction</button>
        </form>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import { useToast } from 'vue-toastification';

const toast = useToast();
const name = ref('');
const amount = ref(0);

const emit = defineEmits(['transactionSubmitted']);

// Hàm xử lý submit
const onSubmit = () => {
    if (name.value && amount.value !== null) {
        const item = {
            name: name.value,
            cost: amount.value
        }
        emit('transactionSubmitted', item);
    } else {
        toast.error('Vui lòng điền nội dung !');
        return;
    }
    name.value = '';
    amount.value = 0;
};


</script>

<style scoped>
#name,
#amount {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    box-sizing: border-box;
}

button {
    background-color: rgb(119, 36, 226);
    color: white;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    cursor: pointer;
    width: 100%;
}

button:hover {
    background-color: rgb(102, 24, 176);
}
</style>
