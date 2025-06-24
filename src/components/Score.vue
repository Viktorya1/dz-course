<script setup>
import IconLike from "../icons/IconLike.vue";

const { score } = defineProps({
  score: String,
});
</script>

<template>
  <div class="header-btn">
    <p>{{ score }}</p>
    <IconLike />
  </div>
</template>

<style scoped>
.header-btn {
  display: flex;
  gap: 10px;
  align-items: center;
  background: var(--color-btn-light);
  color: var(--color-btn);
  font-size: 16px;
  font-family: var(--font);
  font-weight: 700;
  border-radius: 36px;
  padding: 12px 24px;
  box-shadow: 0px 0px 4px 0px rgba(0, 0, 0, 0.15);
}

p {
  margin: 0;
  padding: 0;
}
</style>
