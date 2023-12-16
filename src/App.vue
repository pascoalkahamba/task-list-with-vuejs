<script setup lang="ts">
import { computed, ref } from 'vue'
import Balance from './components/CurrentBalance.vue'
import Header from './components/MyHeader.vue'
import IncomeExpenses from './components/IncomeExpenses.vue'
import TransactionList from './components/TransactionList.vue'
import AddTransaction from './components/addTransaction.vue'

interface TransactionsPrps {
  id: number
  text: string
  amount: string
}

const transactions = ref([
  { id: getUniqueId(), text: 'Food', amount: -200.12 },
  { id: getUniqueId(), text: 'Fruit', amount: 500.12 },
  { id: getUniqueId(), text: 'Clothes', amount: -500.12 },
  { id: getUniqueId(), text: 'Houses', amount: -3000.12 },
  { id: getUniqueId(), text: 'Shirt', amount: 300.12 }
])

function getUniqueId() {
  return Math.round(Math.random() * 10000)
}

const income = computed(() =>
  transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, trans) => {
      return acc + trans.amount
    }, 0)
)

const expense = computed(() =>
  transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, trans) => {
      return acc + trans.amount
    }, 0)
)

const total = computed(() =>
  transactions.value.reduce((acc, trans) => {
    return acc + trans.amount
  }, 0)
)

function addTransaction(transaction: TransactionsPrps) {
  transactions.value.push(...transaction)
  console.log('OK')
}
</script>
<template>
  <section class="container">
    <Header />
    <Balance :total="total" />
    <IncomeExpenses :expense="expense" :income="income" />
    <TransactionList :transactions="transactions" />
    <AddTransaction :handleOnSubmit="addTransaction" />
  </section>
</template>
