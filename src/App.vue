<script>

import TheClock from "./components/TheClock.vue";
import FetchKide from "./components/FetchKide.vue";
import FetchMenuArcada from "./components/FetchMenuArcada.vue";

export default {
  data() {
    return {
      kideUrl: "https://api.kide.app/api/companies/8216a1bc-760d-407b-9c77-5e26a041a25c"
    }
  },
  components: {
    TheClock,
    FetchKide,
    FetchMenuArcada,

  },

  methods:{
    switchOrg(){
      if(this.currentOrg === 0){
        this.currentOrg = 1;
      } else {
        this.currentOrg = 0;
      }
    }
  }
}

</script>

<template>
  <img id="logo" src="src/assets/images/tlklogo-white.png" alt="tlklogo">

  <div id="theClock">
    <TheClock />
    
  </div>
  <div id="theMenu">
    <FetchMenuArcada />
  </div>

  <FetchKide :bim="kideUrl" />

</template>

<style scoped>
#theMenu {
  position: absolute;
  top: 5vh;
  right: 2vw;
  height: fit-content;
  width: fit-content;
  background-color: white;
}
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
  z-index: -1;
  /* kan vara full opacity as well */
}

#theClock {
  position: absolute;
  top: 5vh;
  left: 2vw;
  height: fit-content;
  width: fit-content;
}
</style>
