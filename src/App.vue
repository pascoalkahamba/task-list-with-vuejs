<script setup lang="ts">
import { computed, ref, onMounted } from 'vue';
import Balance from './components/CurrentBalance.vue';
import Header from './components/MyHeader.vue';
import IncomeExpenses from './components/IncomeExpenses.vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/addTransaction.vue';
import { useToast } from 'vue-toastification';

interface TransactionsPrps {
  id: number;
  text: string;
  amount: number;
}

const toast = useToast();
const transactions = ref<TransactionsPrps[]>([]);

onMounted(() => {
  function areThereInLocalStorage() {
    const storageTransactions = JSON.parse(localStorage.getItem('transactions') as string);
    if (storageTransactions) {
      transactions.value = storageTransactions as typeof transactions.value;
    }
  }

  areThereInLocalStorage();
});

function getUniqueId() {
  return Math.round(Math.random() * 10000);
}

const income = computed(() =>
  transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, trans) => {
      return acc + trans.amount;
    }, 0)
);

const expense = computed(() =>
  transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, trans) => {
      return acc + trans.amount;
    }, 0)
);

const total = computed(() =>
  transactions.value.reduce((acc, trans) => {
    return acc + trans.amount;
  }, 0)
);

function saveTransactionsToLocalStorage() {
  localStorage.setItem('transactions', JSON.stringify(transactions.value));
}

function addTransaction(transaction: TransactionsPrps) {
  transactions.value.push({
    id: getUniqueId(),
    text: transaction.text,
    amount: transaction.amount
  });

  saveTransactionsToLocalStorage();
  toast.success('Transaction added');
}

function handleDeleteTransaction(id: number) {
  transactions.value = transactions.value.filter((transaction) => transaction.id !== id);
  saveTransactionsToLocalStorage();
  toast.success('Transaction Deleted');
}
</script>
<template>
  <section class="container">
    <Header />
    <Balance :total="total" />
    <IncomeExpenses :expense="expense" :income="income" />
    <TransactionList :transactions="transactions" @transactionDeleted="handleDeleteTransaction" />
    <AddTransaction @handleOnSubmit="addTransaction" />
  </section>
</template>
