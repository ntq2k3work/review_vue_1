<template>
    <div>
        <h2>History</h2> <hr>
        <ul class="list">
            <li v-for="item in history" :key="item.id">
                <div class="actions">
                    <button @click="handleDelete(item.id)">Delete</button>
                </div>
                <div class="name">{{ item.name }}</div>
                <div class="cost">
                    <p>{{ item.cost }}</p>   
                    <div class="state" :style="{ backgroundColor: colorStage(item) }"></div> 
                </div>
            </li>
        </ul>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

const emit = defineEmits(['deleted']);

const props = defineProps({
    history: {
        type: Array,
        required: true,
    },
});
const colorStage = (item) => {
    return item.cost > 0 ? 'green' : 'red';
};


const handleDelete = (id) => {
    emit('deleted', id);
};

</script>

<style scoped>
ul {
    margin: 0;
    padding: 0;
}

li {
    list-style: none;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #fff;
    padding: 10px 12px;
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
    margin: 12px 0;
    position: relative;
}

.state {
    position: absolute;
    height: 100%;
    width: 0.4rem;
    right: 0;
    top: 0;
}
</style>
