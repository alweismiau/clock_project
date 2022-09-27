<template>
  <h1>Digital Clock</h1>
  <p>Fina Keiza Arismana</p>
  <div class="container">
    <div class="LCD">
      <div class="hours">{{ hours }}</div>
      <div class="divider">:</div>
      <div class="minutes">{{ minutes }}</div>
      <div class="divider">:</div>
      <div class="seconds">{{ seconds }}</div>
    </div>

    <div class="alarm">
      <form name="arlm">
        <span
          ><input type="text" size="2" v-model="alarm.hr" onFocus="select()"
        /></span>
        <span style="font-size: 25px">:</span>
        <span><input type="text" size="2" v-model="alarm.mts" /></span>
        <span style="font-size: 25px">:</span>
        <span><input type="text" size="2" v-model="alarm.ssecs" /></span>
        <br /><br />
        <input type="button" size="2" value="Set Alarm" @click="setAlarm" />
        <input type="button" value="Stop Alarm" @click="stopAlarm" />
      </form>
    </div>
  </div>
</template>
<script>
export default {
  name: "DigitalClock",
  data() {
    return {
      playIt: true,
      // ini buat jam
      hours: 0,
      minutes: 0,
      seconds: 0,

      // audio
      audio: new Audio(
        "https://www.soundjay.com/misc/sounds/bell-ringing-05.mp3"
      ),

      // buat alarm
      alarm: {
        hr: 0,
        mts: 0,
        ssecs: 0,
      },
    };
  },
  mounted() {
    setInterval(() => this.setTime(), 1000);
  },
  methods: {
    setAlarm() {
      var vm = this;
      let hrs = vm.alarm.hr;
      let min = vm.alarm.mts;
      let sec = vm.alarm.ssecs;
      if (vm.hours == hrs && vm.minutes == min && vm.seconds == sec) {
        if (vm.playIt) {
          vm.playmusic();
        }
        return false;
      }
      if (hrs == "") {
        alert("Jam kosong");
        return false;
      }
      if (min == "") {
        alert("Menit kosong");
        return false;
      }
      if (hrs.length == 1) {
        vm.alarm.hr = "0" + hrs;
      }
      if (min.toString().length == 1) {
        vm.alarm.mts = "0" + min;
      }
      if (sec.toString().length == 1) {
        vm.alarm.mts = "0" + min;
      }
      if (hrs.toString().length > 2) {
        alert("Jam yang dimasukkan salah");
        return false;
      }
      if (min.toString().length > 2) {
        alert("Menit yang dimasukkan salah");
        return false;
      }
      if (sec.toString().length > 2) {
        alert("Detik yang dimasukkan salah");
        return false;
      }
      setTimeout(vm.setAlarm, 1000);
    },
    stopAlarm() {
      this.audio.pause();
      this.playIt = false;
      this.audio.loop = this.playIt;
    },
    playmusic() {
      this.audio.play();
      this.audio.loop = this.playIt;
    },
    setTime() {
      const date = new Date();
      let hours = date.getHours();
      let minutes = date.getMinutes();
      let seconds = date.getSeconds();
      hours = hours <= 9 ? `${hours}`.padStart(2, 0) : hours;
      minutes = minutes <= 9 ? `${minutes}`.padStart(2, 0) : minutes;
      seconds = seconds <= 9 ? `${seconds}`.padStart(2, 0) : seconds;
      this.hours = hours;
      this.minutes = minutes;
      this.seconds = seconds;
    },
  },
};
</script>

<style>
  
.LCD {
  display: inline-flex;
}
.LCD > div {
  font-family: "alarm clock";
  font-size: xxx-large;
}
</style>
