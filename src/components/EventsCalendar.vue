<script>

import ical from 'ical';

export default {
    data() {
        return {
            events: [],
        }
    },

    props: {
        bim: String
    },

    methods: {
        async parseIcal(bam) {
            const response = await fetch(bam);
            const ics = await response.text();
            const data = await ical.parseICS(ics);
            const today = new Date()
            for (let k in data) {
                if (data.hasOwnProperty(k)) {
                    var ev = data[k];
                    if (data[k].type == "VEVENT") {
                        const eventStartDate = new Date(ev.start)
                        if (eventStartDate.getDate() === today.getDate() && ev.location) {
                            this.events.push({
                                event: ev.summary,
                                startdate: ev.start, //eller eventStartDate går med båda.
                                endtime: ev.end.toLocaleTimeString("fi-FI"),
                            });
                        }
                    }
                }
            }
            console.log(this.events);
        },

        formatTime(startDate) {
            const date = new Date(startDate);
            const hours = date.getHours().toString().padStart(2, "0");
            const minutes = date.getMinutes().toString().padStart(2, "0");
            return `${hours}:${minutes}`;
        },
        formatEndTime(endTime) {
            const parts = endTime.split(".");
            endTime = parts[0] + ":" + parts[1];
            return endTime;
        },
    },
    mounted() {
        this.parseIcal(this.bim);
    },
}


</script>

<template>
    <div class="events">
        <div class="eventText" v-for="(event, index) in events" :key="index">
            <h2 class="event">{{ event.event }}</h2>

            <div class="timeBar">
                <div class="timeBox">
                    <p class="time">
                        {{ formatTime(event.startdate) }} -
                        {{ formatEndTime(event.endtime) }}
                    </p>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>

*{
    color:white;
}

</style>