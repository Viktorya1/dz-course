<script setup>
import { ref } from "vue";

import Button from "./components/Button.vue";
import Score from "./components/Score.vue";
import Card from "./components/Card.vue";

const API_ENDPOINT = "http://localhost:8080/api/random-words";

let score = ref(100);
let game = ref(false);

let cards = ref();
let error = ref();
let data = ref();
let isLoading = ref(false);

async function getWords() {
  try {
    isLoading.value = true;
    const res = await fetch(`${API_ENDPOINT}`);
    if (res.status != 200) {
      error.value = await res.json();
      data.value = null;
      throw new Error(`HTTP error! status: ${res.status}`);
    }
    error.value = null;
    data.value = await res.json();
    cards.value = data.value.map((item) => ({
      ...item,
      state: "closed",
      cardStatus: "pending",
    }));
  } catch (err) {
    error.value = err.message || "Произошла ошибка при загрузке данных";
    cards.value = [];
    isLoading.value = false;
  }
}

function startGame() {
  game.value = true;
  getWords();
}

console.log(cards);

function handleReverseCard(index) {
  cards.value[index].state = "opened";
}

function handleSelectCard(index, value) {
  cards.value[index].cardStatus = value;
}
</script>

<template>
  <div class="container">
    <header class="header">
      <p class="header-text">Запомни слово</p>
      <Score :score="score" />
    </header>
    <main class="main">
      <Button v-if="game === false" class="start-btn" @click="startGame"
        >Начать игру</Button
      >
      <div v-if="isLoading && game">Загружаем карточки...</div>
      <div v-if="error" class="error-message">{{ error }}</div>
    </main>
    <div v-if="game === true && !isLoading && !error" class="cards">
      <Card
        v-for="(card, index) in cards"
        :key="card.word"
        v-bind="card"
        @reverse-card="() => handleReverseCard(index)"
        @select-card="(value) => handleSelectCard(index, value)"
      />
    </div>
  </div>
</template>

<style scoped>
.container {
  padding: 10px 100px;
}

.main {
  text-align: center;
  margin-top: 10vh;
}

.header {
  display: flex;
  justify-content: space-between;
}

.header-text {
  font-family: var(--font);
  font-size: 16px;
  font-weight: 700;
  text-transform: uppercase;
}

.cards {
  display: flex;
  gap: 20px;
  justify-content: center;
  flex-wrap: wrap;
  margin: 0 auto;
}
</style>
