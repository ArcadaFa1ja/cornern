<script>
import VueQr from 'qrcode.vue';


export default {
    data() {
        return {
            kideData: [],
            imgUrl: "https://portalvhdsp62n0yt356llm.blob.core.windows.net/bailataan-mediaitems/",
            qr: "https://kide.app/events/"
        }
    },
    components: {
        VueQr,
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
    },

}

</script>

<template>
    <div class="container">
        <h2 id="forening" v-html="kideData.model.company.name"></h2>
        <div id="events">
            <div class="event" v-for="event in kideData.model.events" :key="event.id">
                <div class="image-container">
                    <img class="img" :src="imgUrl + event.mediaFilename" />
                    <div class="QR">
                        <VueQr :value="qr + event.id" />
                    </div>
                </div>
                <div class="details">
                    <div class="name">{{ event.name }}</div>
                    <div class="place">{{ event.place }}</div>
                </div>
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

.container {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    background-color: rgba(0, 0, 0, .5);
    color: white;
    border-radius: 10px;
    padding: 0;
    width: 1300px;
    height: 580px;
    box-sizing: border-box;
    overflow-y: auto;
    overflow-x: hidden;
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
    box-sizing: border-box;
    width: 540px;
    border-radius: 10px;
    overflow: hidden;
}


.image-container {
    margin:0;
    padding:0;
    position: relative;
    width: 100%;
    height: 100%;
}

.img {
    position: relative;
    top: 50%;
    left: 50%;
    transform: translate(-50%, 0);
    display: block;
    width: 540px;
    height: auto;
}


.details {
    background-color: rgba(0, 0, 0, .7);
    padding: 10px;
}

.name {
    text-align: center;
    font-size: 35px;

    z-index: 12;
}

.place {
    text-align: center;

}

.QR {
    position: absolute;
    top: 10px;
    right: 10px;
    width: 100px;
    height: 100px;
}
</style>