<script setup lang="ts"></script>
<template>
  <form>
    <h3>Add New Transaction</h3>
    <label for="text">Text</label>
    <input type="text" id="text" />

    <label for="amount">Amount</label>
    <input type="number" id="amount" />
    <span>(negative - expense, posive - income)</span>

    <button type="submit" class="btn">Add Transaction</button>
  </form>
</template>
