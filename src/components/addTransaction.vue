<script setup lang="ts"></script>
<template>
  <form>
    <h3>Add New Transaction</h3>
    <label for="text">Text</label>
    <input type="text" id="text" />

    <label for="amount">Amount</label>
    <input type="number" id="amount" />
    <span>(Aqui vai a descricao)</span>

    <button type="submit" class="btn">Add Transaction</button>
  </form>
</template>
