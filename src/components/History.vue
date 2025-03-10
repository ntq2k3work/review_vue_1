<template>
    <div>
        <h2>History</h2>
        <ul class="list">
            <li v-for="item in history" :key="item.id">
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
import { reactive } from 'vue';

const history = reactive([
    { id: 1, name: 'Item 1', cost: 100 },
    { id: 2, name: 'Item 2', cost: -200 },
    { id: 3, name: 'Item 3', cost: 300 }
]);

const colorStage = (item) => {
    return item.cost > 0 ? 'green' : 'red';
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
