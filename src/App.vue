<script>

import TheClock from "./components/TheClock.vue";
import FetchKide from "./components/FetchKide.vue";
import FetchMenuArcada from "./components/FetchMenuArcada.vue";
import EventsCalendar from "./components/EventsCalendar.vue";

export default {
  data() {
    return {
      kideUrl: "https://api.kide.app/api/companies/8216a1bc-760d-407b-9c77-5e26a041a25c",
      eventCalendar: "https://corsproxy.io/?https://calendar.google.com/calendar/ical/tlk.fi_j78ecj51va7764f75fhkrotsrc%40group.calendar.google.com/public/basic.ics",
      cornerCalendar: "https://corsproxy.io/?https://calendar.google.com/calendar/ical/tlk.fi_nnc4oospos16o4aci02v9o7cr8%40group.calendar.google.com/public/basic.ics"
    }
  },
  components: {
    TheClock,
    FetchKide,
    FetchMenuArcada,
    EventsCalendar,
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

    <div id="componentKide" class="componentBase">
      kide goes here
      <!-- VITTU FUNKAR INTE GENAST MAN STYLAR GÅR DEN SÖNDER
   FÖR NÅGOT ÄR FEL I HUR DESS <template></template> ÄR 
   SETUP ALLTSÅ KODEN DÄR RENDERAR VID FELL TILLFÄLLE ELLER 
   NÅGOT SAKER ÄR INTE GJORDA PÅ KOSHER SÄTT 
   BÖR FIXAS ASAP <FetchKide :bim="kideUrl" /> -->
    </div>

    <div id="componentEventCalendar" class="componentBase">
      <h2>next @ TLK</h2>
      <EventsCalendar :bim="eventCalendar" />
    </div>

    <div id="componentCornerCalendar" class="componentBase">
      <h2>next @ Corner</h2>
      <EventsCalendar :bim="cornerCalendar" />
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
  color: white;
}

.componentBase {
  height: 85%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: rgba(0, 0, 0, .5);
  border-radius: 15px;
  margin:25px;
}

#componentKide {
  flex-basis: 33%;

}

#componentEventCalendar {
  flex-basis: 33%;

}

.componentBase h2{
  margin:50px 0 0 0;
  font-size:40px;
  font-weight: 400;
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
