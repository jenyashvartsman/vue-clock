<template>
  <clock></clock>
</template>

<script>
import Clock from "./components/Clock.vue";
export default {
  components: { Clock },
};
</script>

<style>
:root {
  --primary: rgb(44, 100, 165);
  --background: #060708;
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
  padding: 50px 35px;
  border-radius: 20px;
  background-color: var(--background);
}
</style>
