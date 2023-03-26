<template>
  <div class="wrapper">
    <div class="list">
      <Stopwatch v-for="item in arr"/>
      <StopWatchCreator @click="() => arr.push(1)"/>
    </div>
  </div>
</template>
<script>
import Stopwatch from "@/components/Stopwatch";
import StopWatchCreator from "@/components/StopWatchCreator";

export default {
  components: {
    Stopwatch,
    StopWatchCreator
  },
  data() {
    return {
      arr: [1]
    }
  },
  methods: {

  }
}
</script>
<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
}
body {
  background-color: #353638;
}
.wrapper {
  width: 76%;
  margin: 72px auto;
}
.list {
  margin: 0 auto;
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: flex-start;
  flex-wrap: wrap;
  column-gap: 50px;
}
</style>