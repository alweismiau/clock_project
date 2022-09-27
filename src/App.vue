<template>
  <DigitalClock />
  <Timer />
</template>

<script>
import DigitalClock from "./components/DigitalClock.vue";

export default {
  components: {
    DigitalClock,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin: 0%;
  padding: 0%;
  text-align: center;
}
@font-face {
  font-family: "alarm clock";
  src: url(../public/fonts/alarm.ttf);
}
</style>
