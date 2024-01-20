<script setup lang="ts">
import { defineProps, defineEmits } from 'vue';

interface TransactionsProps {
  id: number;
  text: string;
  amount: number;
}
defineProps<{
  transactions: TransactionsProps[];
 
}>();

const emit = defineEmits(['transactionDeleted']);

function onDeleteTransaction(id: number) {
  emit('transactionDeleted', id);
}
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
        <button
          class="delete-btn"
          @click="onDeleteTransaction(transaction.id)"
          @keyup.alt.space="(key) => console.log(key)"
        >
          X
        </button>
      </li>
    </ul>
  </section>
</template>
