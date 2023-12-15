<script setup lang="ts">
import { defineProps } from 'vue'

defineProps<{
  total: number | string
}>()
</script>
<template>
  <section>
    <h4>Your Balance</h4>
    <h1>${{ total }}</h1>
  </section>
</template>
