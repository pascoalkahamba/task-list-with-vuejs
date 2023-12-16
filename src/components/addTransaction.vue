<script setup lang="ts">
import { defineProps, defineEmits, ref } from 'vue'
import { useToast } from 'vue-toastification'
interface TransactionsPrps {
  id: number
  text: string
  amount: string
}

const toast = useToast()

defineProps<{
  handleOnSubmit: (transactions: TransactionsPrps) => void
}>()

const emit = defineEmits(['handleOnSubmit'])
const text = ref('')
const amount = ref('')

function isEmpty() {
  if (!text.value || !amount.value) {
    return toast.error('Both fields must be filled!')
  }
  text.value = ''
  amount.value = ''
}
const transactionData = { text: text.value, amount: amount.value }
function onSubmit() {
  console.log(text.value, amount.value)
  isEmpty()
  emit('handleOnSubmit', transactionData)
}
</script>
<template>
  <form @submit.prevent="onSubmit">
    <h3>Add New Transaction</h3>
    <label for="text">Text</label>
    <input type="text" id="text" v-model="text" />

    <label for="amount">Amount</label>
    <input type="text" id="amount" v-model="amount" />
    <span>(negative - expense, posive - income)</span>

    <button type="submit" class="btn">Add Transaction</button>
  </form>
</template>
