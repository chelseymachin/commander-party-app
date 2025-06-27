<template>
  <header>
    <div class="wrapper">
      <HeaderBar />
    </div>
  </header>
  <main>
    <DeckInput @submit="console.log('Deck submitted!')" />
  </main>
</template>
<script setup>
import HeaderBar from './components/HeaderBar.vue'
import DeckInput from './components/DeckInput.vue'
</script>
<style scoped></style>
