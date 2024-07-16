<script setup>
import { ref } from 'vue'

const helloA = ref('Status is true');
const helloB = ref('Status is false');
const status = ref(false);
const jobs = ref(['clerk', 'accountant', 'manager']);
const link = ref('https://google.com');
const countdown = ref(1);
const percentage = ref(50);
const perColor = ref('yellow');

const add = () => {
  countdown.value = countdown.value + 1;
};

const increase = () => {
  if (percentage.value != 100) {
    percentage.value = percentage.value + 10;
  }
  percentageColor();
}

const decrease = () => {
  if (percentage.value != 0) {
    percentage.value = percentage.value - 10;
  }
  percentageColor();
}

const percentageColor = () => {
  if (percentage.value <= 30) {
    perColor.value = 'red';
  } else if (percentage.value > 30 && percentage.value <= 70) {
    perColor.value = 'yellow';
  } else {
    perColor.value = 'green'
  }
}
</script>

<template>
  <h2>Script using Composition API</h2>
  <p v-if="status">{{ helloA }}</p>
  <p v-else>{{ helloB }}</p>
  <ul>
    <li v-for="job in jobs" :key="job">{{ job }}</li>
  </ul>
  <a v-bind:href="link">Click to go Google</a>
  <p style="margin-top: 10px;">Countdown: {{ countdown }}</p>
  <button @click="add">Add</button>
  <div class="div-style">
    <div class="internal-div-style" :style="{ width: percentage + '%', backgroundColor: perColor }">
      {{ percentage != 0 ? percentage : '' }}
    </div>
  </div>
  <button @click="increase">Increase 10%</button>
  <button @click="decrease">Decrease 10%</button>
</template>

<style>
.div-style {
  margin-top: 20px;
  border: 1px solid black;
  width: 100%;
  height: 50px;
  display: flex;
}

.internal-div-style {
  width: 50%;
  background-color: yellow;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>