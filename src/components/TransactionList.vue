<script setup lang="ts">
import { defineProps } from 'vue'

interface TransactionsProps {
  id: number
  text: string
  amount: number
}
defineProps<{
  transactions: TransactionsProps[]
}>()
</script>

<template>
  <section>
    <h3>History</h3>
    <ul class="list">
      <li
        :class="transaction.amount > 0 ? 'plus' : 'minus'"
        v-for="transaction in transactions"
        :key="transaction.id"
      >
        <span>{{ transaction.text }}</span>
        <span>${{ transaction.amount }}</span>
        <button class="delete-btn">X</button>
      </li>
    </ul>
  </section>
</template>
