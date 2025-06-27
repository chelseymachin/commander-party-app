<template>
  <div class="deck-input-wrapper">
    <label for="deckInput" class="deck-label">Paste Your Decklist</label>
    <textarea
      id="deckInput"
      v-model="deckText"
      placeholder="Paste your decklist here. One card per line.\nFirst line must be your commander!"
      class="deck-textarea"
    ></textarea>
    <div class="card-count">{{ cardCount }} card{{ cardCount !== 1 ? 's' : '' }} detected</div>
    <NeoButton @click="emitSubmit">Analyze Deck!</NeoButton>
  </div>
</template>

<script setup>
import { ref, computed, defineEmits } from 'vue'
import NeoButton from './NeoButton.vue'

const emits = defineEmits(['submit'])

const deckText = ref('')

const cardCount = computed(
  () =>
    deckText.value
      .split('\n')
      .map((line) => line.trim())
      .filter((line) => line.length > 0).length,
)

const emitSubmit = () => {
  emits('submit', deckText.value)
  console.log(`Deck submitted: ${deckText.value}`)
}
</script>

<style scoped>
.deck-input-wrapper {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 700px;
  margin: 2rem auto;
  font-family: 'Nunito', sans-serif;
}

.deck-label {
  font-size: 1.25rem;
  font-weight: 800;
  color: var(--charcoal-gray);
}

.deck-textarea {
  background-color: white;
  border: 4px solid black;
  box-shadow: 4px 4px 0 black;
  border-radius: 12px;
  padding: 1rem;
  font-size: 1rem;
  font-family: 'Nunito', sans-serif;
  resize: vertical;
  min-height: 250px;
  outline: none;
  transition: border-color 0.3s;
  color: var(--charcoal-gray);
}

.deck-textarea::placeholder {
  color: #888;
  white-space: pre-line;
}

.card-count {
  font-size: 1rem;
  font-weight: bold;
  color: var(--charcoal-gray);
  text-align: right;
  padding-right: 0.25rem;
}
</style>
