<script setup lang="ts">
import { defineProps } from 'vue'

defineProps<{
  total: number
}>()
</script>
<template>
  <section>
    <h4>Your Balance</h4>
    <h1>${{ Math.abs(total).toFixed(2) }}</h1>
  </section>
</template>
