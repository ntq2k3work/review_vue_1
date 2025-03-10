<script setup>
import Header from "./components/Header.vue";
import Balance from "./components/Balance.vue";
import Fluctuation from "./components/Fluctuation.vue";
import History from "./components/History.vue";
</script>

<template>
  <header>
    <Header />
  </header>

  <main>
    <Balance />
    <Fluctuation />
    <History />
  </main>
</template>

<style scoped>

</style>
