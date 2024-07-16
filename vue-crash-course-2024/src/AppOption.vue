<script>
export default {
  data() {
    return {
      helloA: "status is true",
      helloB: "status is false",
      status: false,
      jobs: ['clerk', 'accountant', 'manager'],
      link: 'https://google.com',
      countdown: 1
    }
  },
  methods: {
    add() {
      this.countdown = this.countdown + 1
    }
  }
}
</script>

<template>
  <h2>Script using Option API</h2>
  <p v-if="status">{{ helloA }}</p>
  <p v-else>{{ helloB }}</p>
  <ul>
    <li v-for="job in jobs" :key="job">{{ job }}</li>
  </ul>
  <a v-bind:href="link">Click to go Google</a>
  <p style="margin-top: 10px;">Countdown: {{ countdown }}</p>
  <button @click="add">Add</button>
</template>