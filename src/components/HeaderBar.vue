<template>
  <header class="header-bar">
    <div class="logo-container">
      <span class="icon">🧙‍♀️✨</span>
      <h1 class="title">Commander Party</h1>
    </div>
  </header>
</template>

<script setup></script>

<style scoped>
.header-bar {
  color: var(--charcoal-gray);
  padding: 1.5rem 2rem;
  width: 100%;
  position: relative;
}

.logo-container {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
  max-width: 1400px;
  margin: 0 auto;
}

.title {
  font-size: 2.5rem;
  font-weight: 800;
  margin: 0;
  color: var(--charcoal-gray);
  letter-spacing: -0.02em;
}

.icon {
  font-size: 2.5rem;
  transform: rotate(-8deg);
  filter: drop-shadow(2px 2px 0px var(--charcoal-gray));
  animation: bounce 2s ease-in-out infinite;
}

/* Fun bounce animation for the icon */
@keyframes bounce {
  0%,
  20%,
  50%,
  80%,
  100% {
    transform: rotate(-8deg) translateY(0);
  }
  40% {
    transform: rotate(-8deg) translateY(-8px);
  }
  60% {
    transform: rotate(-8deg) translateY(-4px);
  }
}

/* Mobile responsiveness */
@media (max-width: 768px) {
  .header-bar {
    padding: 1rem 1.5rem;
  }

  .title {
    font-size: 2rem;
  }

  .icon {
    font-size: 2rem;
  }
}

@media (max-width: 480px) {
  .logo-container {
    gap: 0.75rem;
  }

  .title {
    font-size: 1.75rem;
  }

  .icon {
    font-size: 1.75rem;
  }
}
</style>
