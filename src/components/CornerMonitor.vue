<script>

export default {
    data() {
        return {
            events: this.cornerEvent,
        }
    },

    props: {
        cornerEvent: Array,
    },

    methods: {
        
    },
    mounted() {
        console.log(this.events)
    },
}


</script>

<template>
    
    <div id="monitor">
        <div class="eventText">
            <h2 class="event" v-html="events[0].event"></h2>
            <p class="date" v-html="events[0].date"></p>
            <div class="timeBar">
                <div class="timeBox">
                    <p class="time"></p>
                </div>
            </div>
        </div>
    </div>

</template>

<style scoped>

#monitor{
    display:block;
    width:90%;
    height:90%;
    background-color: red;

}

</style>