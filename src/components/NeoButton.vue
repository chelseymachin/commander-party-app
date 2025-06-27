<template>
  <button class="neo-btn" :class="variantClass" @click="$emit('click')">
    <slot />
  </button>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  variant: {
    type: String,
    default: 'coral',
    validator: (value) => ['coral', 'blue', 'yellow'].includes(value),
  },
})

const variantClass = computed(() => {
  return {
    coral: 'bg-coral text-white',
    blue: 'bg-blue text-charcoal',
    yellow: 'bg-yellow text-charcoal',
  }[props.variant]
})
</script>

<style scoped>
.neo-btn {
  border: 4px solid black;
  padding: 12px 24px;
  font-weight: 900;
  font-family: 'Nunito', sans-serif;
  font-size: 1.2rem;
  border-radius: 0.5rem;
  box-shadow: 4px 4px 0px black;
  cursor: pointer;
  transition:
    transform 0.1s ease,
    box-shadow 0.1s ease;
}

/* active and hover states */
.neo-btn:hover {
  transform: translate(-1px, -1px);
  box-shadow: 5px 5px 0px black;
}

.neo-btn:active {
  transform: translate(2px, 2px);
  box-shadow: 1px 1px 0px black;
}

/* Variant background colors */
.bg-coral {
  background-color: var(--coral-pink);
}

.bg-blue {
  background-color: var(--sage-green);
}

.bg-yellow {
  background-color: var(--bright-yellow);
}

/* Variant text colors */
.text-charcoal {
  color: var(--charcoal-gray);
}

.text-white {
  color: #fff5ee;
}
</style>
