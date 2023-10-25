<script>

import TheClock from "./components/TheClock.vue";

export default {
  components: {
    TheClock
  },
}

</script>

<template>
  <img id="logo" src="src/assets/images/tlklogo-white.png" alt="tlklogo">

  <div id="theClock">
    <TheClock />
  </div>
</template>

<style scoped>


#logo {
  max-width: 100%;
  height: auto;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  height: 500px;
  width: 500px;
  opacity: 0.3;
  /* kan vara full opacity as well */
}

#theClock{
  position: absolute;
  top: 5vh;
  left: 2vw;
  height: fit-content;
  width: fit-content;
}

</style>
