<template>
  <div class="main">
    <img src="../assets/add_btn.png" alt="Add stopwatch">
  </div>
</template>
<script>
export default {

}
</script>
<style scoped>
.main {
  background-color: #696969;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  width: 225px;
  height: 120px;
  margin-bottom: 45px;
  min-width: 225px;
}
.main {
  cursor: pointer;
  transition: .2s;
}
.main:hover {
  opacity: .6;
}
</style>