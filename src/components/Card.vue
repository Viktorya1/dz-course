<script setup>
import IconFail from "../icons/IconFail.vue";
import IconSuccess from "../icons/IconSuccess.vue";

const props = defineProps({
  word: String,
  translation: String,
  state: String,
  cardStatus: String,
});

const emit = defineEmits(["reverseCard", "selectCard"]);

function reverse() {
  emit("reverseCard");
}

function select() {
  emit("selectCard");
  cardStatus = "success";
}
</script>

<template>
  Перевод: {{ translation }} <br />
  Состояние: {{ state }} <br />
  Статус: {{ cardStatus }}
  <div class="card">
    <div class="card-wrapper">
      <span class="card-number">01</span>
      <p class="card-word">{{ word }}</p>
      <button @click="reverse()" class="card-btn">Перевернуть</button>
    </div>
  </div>

  <div class="card">
    <div class="card-wrapper">
      <span class="card-number">01</span>
      <p class="card-word">{{ translation }}</p>
      <div class="btn-reverse">
        <button class="icon-btn"><IconFail /></button>
        <button @click="select()" class="icon-btn"><IconSuccess /></button>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="card-wrapper">
      <span class="card-number">01</span>
      <span><IconSuccess class="status-icon" /></span>
      <p class="card-word">Перевод</p>
      <button class="card-btn">Завершено</button>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 250px;
  height: 376px;
  border-radius: 16px;
  background: var(--color-primary-inverted);
  box-shadow: 0px 0px 16px 0px rgba(0, 0, 0, 0.1);
  padding: 28px 19px;
}

.card-wrapper {
  border: 1px solid var(--color-outlined);
  border-radius: 12px;
  height: 100%;
  width: 100%;
  position: relative;
}

.card-number {
  font-size: 14px;
  font-weight: 400;
  font-family: var(--font);
  position: absolute;
  top: -9px;
  left: 16px;
  background: var(--color-primary-inverted);
}

.card-word {
  text-align: center;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  left: 50%;
  transform: translateX(-50%);
  font-size: 18px;
  font-weight: 400;
  font-family: var(--font);
}

.card-btn {
  position: absolute;
  bottom: -9px;
  border: none;
  background: var(--color-primary-inverted);
  left: 50%;
  transform: translateX(-50%);
  font-size: 12px;
  font-weight: 700;
  font-family: var(--font);
  cursor: pointer;
}

.btn-reverse {
  display: flex;
  justify-content: space-between;
  width: 90px;
  position: absolute;
  bottom: -16px;
  background: var(--color-primary-inverted);
  left: 50%;
  transform: translateX(-50%);
}

.icon-btn {
  border: none;
  padding: 0;
  background: var(--color-primary-inverted);
  cursor: pointer;
}

.status-icon {
  width: 48px;
  height: 48px;
  position: absolute;
  top: -25px;
  left: 50%;
  transform: translateX(-50%);
  background: var(--color-primary-inverted);
}
</style>
