<template>
  <div class="clock-wrapper">
    <div class="date">{{ getDateStr }}</div>
    <div class="clock">
      <div class="time">
        <clock-digit :digit="getFirstDigit(now.getHours())"></clock-digit>
        <clock-digit :digit="getSecondDigit(now.getHours())"></clock-digit>
      </div>
      <div class="seperator">
        <div></div>
        <div></div>
      </div>
      <div class="time">
        <clock-digit :digit="getFirstDigit(now.getMinutes())"></clock-digit>
        <clock-digit :digit="getSecondDigit(now.getMinutes())"></clock-digit>
      </div>
      <div class="seperator">
        <div></div>
        <div></div>
      </div>
      <div class="time">
        <clock-digit :digit="getFirstDigit(now.getSeconds())"></clock-digit>
        <clock-digit :digit="getSecondDigit(now.getSeconds())"></clock-digit>
      </div>
    </div>
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
  computed: {
    getDateStr() {
      return (
        this.now.toLocaleDateString("default", { weekday: "long" }) +
        ", " +
        this.now.toLocaleString("default", { month: "long" }) +
        " " +
        this.now.getDate() +
        ", " +
        this.now.getFullYear()
      );
    },
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
.clock-wrapper {
  background-color: var(--background-clock);
  padding: 50px 30px;
  border-radius: 20px;
}

.date {
  text-align: center;
  margin-bottom: 60px;
  font-size: 36px;
  font-weight: 500;
}

.clock {
  display: flex;
  align-items: center;
}

.clock .time {
  display: flex;
}

.clock .seperator div {
  width: 20px;
  height: 20px;
  background-color: var(--primary);
  border-radius: 50%;
  margin: 40px 20px;
}
</style>