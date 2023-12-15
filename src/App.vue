<script setup lang="ts">
import { ref } from 'vue'
import Balance from './components/CurrentBalance.vue'
import Header from './components/MyHeader.vue'
import IncomeExpenses from './components/IncomeExpenses.vue'
import TransactionList from './components/TransactionList.vue'
import AddTransaction from './components/addTransaction.vue'

const transactions = ref([
  { name: 'Food', price: 200.12 },
  { name: 'Fruit', price: 300.12 },
  { name: 'Clothes', price: 500.12 },
  { name: 'Houses', price: 2000.12 },
  { name: 'Shirt', price: 100.12 }
])
</script>
<template>
  <section class="container">
    <Header />
    <Balance />
    <IncomeExpenses />
    <TransactionList />
    <AddTransaction />
  </section>
</template>
