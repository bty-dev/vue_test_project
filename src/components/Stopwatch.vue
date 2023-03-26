<template>
  <div class="stopwatch">
    <div class="time" :style="[running ? {color: '#fff'} : {color: '#9E9E9E'}]">
      {{time.hours !== null ? `${time.hours} :` : ""}}
      {{time.minutes !== null ? `${time.minutes} :` : ""}}
      {{time.seconds}}
    </div>
    <div class="delimiter" :style="[running ? {backgroundColor: '#fff'} : {backgroundColor: '#9E9E9E'}]">

    </div>
    <div class="controls">
      <img :style="[!running ? {opacity: .4} : {}]" v-if="!running" @click="() => this.running = !this.running" src="../assets/play_btn.png" alt="Play">
      <img :style="[!running ? {opacity: .4} : {}]" style="width: 17px; height: 20px" v-else @click="() => this.running = !this.running" src="../assets/pause_btn.png" alt="Pause">
      <img :style="[!running ? {opacity: .4} : {}]" @click="stopTime" src="../assets/stop_btn.png" alt="Stop">
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      time: {
        hours: null,
        minutes: null,
        seconds: 0,
      },
      timer: null,
      running: false,
    }
  },
  methods: {
    startTime() {
      this.timer = setInterval(() => {
        if (this.time.seconds < 59) this.time.seconds++;
        else {
          this.time.seconds = 0;
          this.time.minutes++;
        }
        if (this.time.minutes === 60) {
          this.time.hours++;
          this.time.minutes = 0;
        }
      }, 1000);
    },
    pauseTime() {
      clearInterval(this.timer);
    },
    stopTime() {
      clearInterval(this.timer);
      this.time.hours = null;
      this.time.minutes = null;
      this.time.seconds = 0;
      this.running = false;
    }
  },
  watch: {
    running:  function (newVal, oldVal) {
      if (newVal) this.startTime();
      else this.pauseTime();
    }
  }
}
</script>
<style>
.stopwatch {
  background-color: #696969;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  width: 225px;
  min-width: 225px;
  height: 120px;
  margin-bottom: 45px;
}
.time {
  text-align: center;
  color: #9E9E9E;
  font-size: 22px;
  padding: 10px 0;
}
.delimiter {
  width: 100%;
  height: 1px;
  background-color: #9E9E9E;
}
.controls {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  padding: 10px 0;
}
.controls > img {
  cursor: pointer;
  transition: .2s;
}
.controls > img:hover {
  opacity: 1;
}
</style>