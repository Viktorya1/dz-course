<script setup></script>

<template>
  <button class="btn"><slot></slot></button>
</template>

<style scoped>
.btn {
  border: none;
  border-radius: 100px;
  background: var(--color-btn);
  color: var(--color-primary-inverted);
  font-family: var(--font);
  font-size: 24px;
  font-weight: 400;
  text-align: center;
  cursor: pointer;
  padding: 16px 40px;
}

.btn:hover {
  background: var(--color-btn-hover);
}
</style>
