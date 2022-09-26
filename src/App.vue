<template>
  <DigitalClock/>
  <!-- <AlarmClock/> -->
</template>

<script>
import DigitalClock from "./components/DigitalClock.vue"
// import AlarmClock from "./components/AlarmClock.vue"
export default {
  components: {
    DigitalClock,
    // AlarmClock
}
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
}
@font-face {
  font-family: "alarm clock";
  src: url(../public/fonts/alarm.ttf);
}
</style>
