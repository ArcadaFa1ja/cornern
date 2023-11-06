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

  methods: {

  }
}

</script>

<template>
  <img id="logo" src="src/assets/images/tlklogo-white.png" alt="tlklogo">

  <div id="theClock">
    <TheClock />
  </div>

  <div id="componentMaster">

    <!--<div id="componentMenu">
      <FetchMenuArcada />
    </div>
    -->

    <div id="componentKide">
      kide goes here
      <!-- VITTU FUNKAR INTE GENAST MAN STYLAR GÅR DEN SÖNDER
   FÖR NÅGOT ÄR FEL I HUR DESS <template></template> ÄR 
   SETUP ALLTSÅ KODEN DÄR RENDERAR VID FELL TILLFÄLLE ELLER 
   NÅGOT SAKER ÄR INTE GJORDA PÅ KOSHER SÄTT 
   BÖR FIXAS ASAP <FetchKide :bim="kideUrl" /> -->
    </div>

    <div id="componentEventCalendar">
      event calendar goes here
    </div>

    <div id="componentCornerCalendar">
      corner calendar goes here
    </div>


  </div>
</template>

<style scoped>
#componentMaster {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: row;
  align-items: center;
  text-align: center;
}

#componentKide {
  flex-basis: 33%;
}

#componentEventCalendar {
  flex-basis: 33%;
}

#componentCornerCalendar {
  flex-basis: 50%;
}

#componentMenu {
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
