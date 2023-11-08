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
                        if (eventStartDate > today) {
                            this.events.push({
                                event: ev.summary,
                                startdate: ev.start, //eller eventStartDate går med båda.
                                endtime: ev.end.toLocaleTimeString("fi-FI"),
                                date: ev.start.toLocaleDateString("fi-FI"),
                            });
                        }
                    }
                }
            }
            console.log(this.events);
            this.sortArray(this.events);
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

        sortArray(obj) {
            obj.sort(function (a, b) {
                return new Date(a.startdate) - new Date(b.startdate);
            });
        }
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
            <p class="date">{{ event.date }}</p>
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
.events {
    height: 100%;
    width:85%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.eventText {
    color: black;
    width: 100%;
    padding: 20px;
    border-radius: 15px;
    border: 5px solid #000000;
    background-color: white;
}

.event {
    color: #151877;
}

p,
h2 {
    margin: 0;
    line-height: 1;
    font-size: 20px;
}

h2 {
    font-size: 30px;
}

.time {
    margin-top: 10px;
    font-size: 30px;
}
</style>