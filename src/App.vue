<script setup>
import Button from "./components/Button.vue";
import Score from "./components/Score.vue";
import Card from "./components/Card.vue";
const score = 100;

function getSelect(status) {
  console.log(status);
}
</script>

<template>
  <header class="header">
    <p class="header-text">Запомни слово</p>
    <Score :score="score" />
  </header>
  <main class="main">
    <Button class="start-btn">Начать игру</Button>
  </main>
  <Card @reverse-card="getSelect" @select-card="getSelect" />
</template>

<style scoped>
.main {
  text-align: center;
  margin-top: 30vh;
}

.header {
  display: flex;
  justify-content: space-around;
  margin-top: 50px;
}

.header-text {
  font-family: var(--font);
  font-size: 16px;
  font-weight: 700;
  text-transform: uppercase;
}
</style>
