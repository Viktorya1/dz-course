<script setup>
let data = new Date();

var months = [
  "January",
  "February",
  "March",
  "April",
  "May",
  "June",
  "July",
  "August",
  "September",
  "October",
  "November",
  "December",
];

let date = data.getDate();
let nowMonth = data.getMonth();
let year = data.getFullYear();
</script>

<template>
  <h2>{{ date }} {{ months[Number(nowMonth)] }} {{ year }}</h2>
</template>

<style scoped></style>
