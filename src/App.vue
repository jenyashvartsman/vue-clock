<template>
  <clock></clock>
  <button class="btn-theme" @click="toggleTheme">&#9728;</button>
</template>

<script>
import Clock from "./components/Clock.vue";
export default {
  components: { Clock },
  methods: {
    toggleTheme() {
      document.getElementById("app").classList.toggle("dark");
    },
  },
};
</script>

<style>
:root {
  --primary: #3f51b5;
  --background-app: #fafafa;
  --background-clock: #303030;
  --digit-w: 100px;
  --digit-h: 200px;
  --digit-line-w: 10px;
}

body {
  padding: 0;
  margin: 0;
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
}

#app {
  font-family: sans-serif, Helvetica, Arial;
  color: var(--primary);
  height: 100%;
  width: 100%;
  background-color: var(--background-app);
  display: flex;
  align-items: center;
  justify-content: center;
}

#app.dark {
  --primary: #4b95e9;
  --background-app: #303030;
  --background-clock: #494949;
}

#app .btn-theme {
  position: fixed;
  bottom: 20px;
  right: 20px;
  border: none;
  border-radius: 50%;
  width: 64px;
  height: 64px;
  font-size: 32px;
  line-height: 36px;
  background-color: var(--background-clock);
  color: var(--primary);
  cursor: pointer;
}

@media only screen and (max-width: 850px) {
  :root {
    --digit-w: 25px;
    --digit-h: 50px;
    --digit-line-w: 6px;
  }

  .clock-wrapper {
    padding: 25px;
  }

  .clock-wrapper .time {
    flex-direction: column;
  }

  .clock-wrapper .date {
    font-size: 18px;
  }

  .clock-wrapper .time-num {
    margin: 10px 0;
  }

  .clock-wrapper .time-seperator {
    display: none;
  }
}

@media only screen and (min-width: 850px) and (max-width: 1200px) {
  :root {
    --digit-w: 50px;
    --digit-h: 100px;
    --digit-line-w: 8px;
  }
}

@media only screen and (min-width: 1200px) {
  :root {
    --digit-w: 100px;
    --digit-h: 200px;
  }
}
</style>
