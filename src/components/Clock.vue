<template>
  <div class="clock">
    <clock-digit :digit="getFirstDigit(now.getHours())"></clock-digit>
    <clock-digit :digit="getSecondDigit(now.getHours())"></clock-digit>
    <div class="seperator">
      <div></div>
      <div></div>
    </div>
    <clock-digit :digit="getFirstDigit(now.getMinutes())"></clock-digit>
    <clock-digit :digit="getSecondDigit(now.getMinutes())"></clock-digit>
    <div class="seperator">
      <div></div>
      <div></div>
    </div>
    <clock-digit :digit="getFirstDigit(now.getSeconds())"></clock-digit>
    <clock-digit :digit="getSecondDigit(now.getSeconds())"></clock-digit>
  </div>
</template>

<script>
import ClockDigit from "./ClockDigit.vue";
export default {
  components: { ClockDigit },
  data() {
    return {
      now: new Date(),
    };
  },
  beforeMount() {
    setInterval(() => (this.now = new Date()), 1000);
  },
  methods: {
    getFirstDigit(num) {
      return Math.floor(num / 10);
    },
    getSecondDigit(num) {
      return num > 9 ? num % 10 : num;
    },
  },
};
</script>

<style>
.clock {
  display: flex;
  align-items: center;
}

.clock .seperator div {
  width: 20px;
  height: 20px;
  background-color: var(--primary);
  border-radius: 50%;
  margin: 40px 20px;
}
</style>