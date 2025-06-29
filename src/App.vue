<script setup>
import { ref } from "vue";

import Button from "./components/Button.vue";
import Score from "./components/Score.vue";
import Card from "./components/Card.vue";

let score = ref(100);

let cards = ref([
  {
    word: "Home",
    translation: "Дом",
    state: "closed",
    cardStatus: "pending",
  },
  {
    word: "Car",
    translation: "Машина",
    state: "closed",
    cardStatus: "pending",
  },
]);

function handleReverseCard(index) {
  cards.value[index].state = "opened";
}

function handleSelectCard(index) {
  cards.value[index].cardStatus = "success";
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
  <Card
    v-for="(card, index) in cards"
    :key="card.word"
    v-bind="card"
    @reverse-card="() => handleReverseCard(index)"
    @select-card="() => handleSelectCard(index)"
  />
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
