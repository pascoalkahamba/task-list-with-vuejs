<script setup lang="ts">
import { defineProps } from 'vue'

defineProps<{
  income: number
  expense: number
}>()
</script>
<template>
  <section class="inc-exp-container">
    <div class="money">
      <h4>Income</h4>
      <span class="plus">${{ income.toFixed(2) }}</span>
    </div>
    <div class="money">
      <h4>Expense</h4>
      <span class="minus">${{ Math.abs(expense).toFixed(2) }}</span>
    </div>
  </section>
</template>
