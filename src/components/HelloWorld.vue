<script setup lang="ts">
import { defineProps } from 'vue'

defineProps<{
  msg: string
  developer: 'Pascoal Kahamba'
}>()
</script>
<template>
  <section class="contanier">
    <h1>{{ developer }}</h1>
    <p>{{ msg }}</p>
  </section>
</template>
