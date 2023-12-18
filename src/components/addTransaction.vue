<script setup lang="ts">
import { defineProps, defineEmits, ref } from 'vue';
import { useToast } from 'vue-toastification';
interface TransactionsPrps {
  id: number;
  text: string;
  amount: number;
}

const toast = useToast();

defineProps<{
  handleOnSubmit?: (transactions: TransactionsPrps) => void;
}>();

const emit = defineEmits(['handleOnSubmit']);
const text = ref('');
const amount = ref('');

function onSubmit() {
  if (!text.value || !amount.value) {
    toast.error('Both fields must be filled!');
    return;
  }

  const transactionData = { text: text.value, amount: parseFloat(amount.value) };
  emit('handleOnSubmit', transactionData);
  text.value = '';
  amount.value = '';
}
</script>
<template>
  <form @submit.prevent="onSubmit">
    <h3>Add New Transaction</h3>
    <label for="text">Text</label>
    <input type="text" id="text" v-model="text" />

    <label for="amount">Amount</label>
    <input type="number" id="amount" v-model="amount" />
    <span>(negative - expense, posive - income)</span>

    <button type="submit" class="btn">Add Transaction</button>
  </form>
</template>
