<template>
  <div class="clock-wrapper">
    <div class="date">{{ getDateStr }}</div>
    <div class="time">
      <div class="time-num">
        <clock-digit :digit="getFirstDigit(now.getHours())"></clock-digit>
        <clock-digit :digit="getSecondDigit(now.getHours())"></clock-digit>
      </div>
      <div class="time-seperator">
        <div></div>
        <div></div>
      </div>
      <div class="time-num">
        <clock-digit :digit="getFirstDigit(now.getMinutes())"></clock-digit>
        <clock-digit :digit="getSecondDigit(now.getMinutes())"></clock-digit>
      </div>
      <div class="time-seperator">
        <div></div>
        <div></div>
      </div>
      <div class="time-num">
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

.clock-wrapper .date {
  text-align: center;
  margin-bottom: 60px;
  font-size: 36px;
  font-weight: 500;
}

.clock-wrapper .time {
  display: flex;
  align-items: center;
}

.clock-wrapper .time .time-num {
  display: flex;
}

.clock-wrapper .time .time-seperator div {
  width: calc(var(--digit-w) / 5);
  height: calc(var(--digit-w) / 5);
  background-color: var(--primary);
  border-radius: 50%;
  margin: 40px 20px;
}
</style>