<script setup lang="ts">
import Header from './components/Header.vue'
import IncomeExpenses from './components/IncomeExpenses.vue'
import TransactionList from './components/TransactionList.vue'
import AddTransaction from './components/addTransaction.vue'
</script>
<template>
  <section class="container">
    <Header />
    <IncomeExpenses />
    <TransactionList />
    <AddTransaction />
  </section>
</template>
