<script>

export default {
    data() {
        return {
            kideData: [],
            imgUrl: "https://portalvhdsp62n0yt356llm.blob.core.windows.net/bailataan-mediaitems/"
        }
    },

    props: {
        bim: String
    },

    methods: {
        async fetchApi(bim) {
            console.log("fetchApi()");
            const res = await fetch(bim);
            const data = await res.json();
            this.kideData = data;
            console.log(this.kideData);
        },
    },
    created() {
        this.fetchApi(this.bim);
    }
}

</script>

<template>
    <div class="container">
        <h2 id="forening" v-html="kideData.model.company.name"></h2>
        <div id="events">
            <div class="event" v-for="event in kideData.model.events" :key="event.id">
                <img class="img" :src="imgUrl + event.mediaFilename">
                <div class="name">{{ event.name }}</div>
                <div class="place">{{ event.place }}</div>
            </div>
        </div>
    </div>
</template>

<style scoped>
h2 {
    font-size: 40px;
    margin: 0;
    text-align: center;
}

.img {
    display: block;
    width: 500px;
    height: auto;
}

.container {
    display: flex;
    flex-direction: column;
    background-color: rgba(0, 0, 0, .5);
    color: white;
    border-radius: 10px;
    padding: 50px;
    width: 1300px;
    height: 580px;
    box-sizing: border-box;
    overflow-y: auto;
    overflow-x:hidden;
    -ms-overflow-style: none;
    /* IE and Edge */
    scrollbar-width: none;
    /* Firefox */
    
}
.container::-webkit-scrollbar {
        display: none;
    }

#events {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-evenly;
    align-items: center;
}

.event {
    background-color: rgba(0, 0, 0, .5);
    display: block;
    font-size: 30px;
    padding: 20px;
    margin: 10px;
    border-radius: 10px;
}

.event:hover{
    cursor: pointer;
    transform: scale(1.1);
    transition: 0.1s;
}

.name {
    text-align: center;
    font-size: 35px;
}

.place {
    text-align: center;
}</style>