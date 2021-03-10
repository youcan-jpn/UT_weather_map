<template>
    <div class="campus-panel">
        <h2>{{ eng2kanji(area) }}</h2>
        <div class="container">
            <WeatherInfoItem v-for="item in info.data.list" :key="item.dt" :item="item" class="item" />
        </div>
    </div>
</template>

<script>
import WeatherInfoItem from './WeatherInfoItem.vue'

const axios = require('axios')
const apikey = ''
// githubに載せないように注意

export default {
    name: "WeatherInfo",
    props: {
        area: String
    },
    components: {
        WeatherInfoItem
    },
    data () {
        return {
            info: null,
            areadata: {
                hongo: {
                    lat: 35.712694,
                    lon: 139.761778,
                },
                komaba: {
                    lat: 35.660111,
                    lon: 139.684667,
                },
                kashiwa: {
                    lat: 35.900889,
                    lon: 139.936917,
                }
            }
        }
    },
    methods: {
        eng2kanji: function(area) {
            if (area === 'hongo') {
                return "本郷"
            } else if (area === 'komaba') {
                return "駒場"
            } else if (area === 'kashiwa') {
                return "柏"
            } else {
                return "不明"
            }
        },
        getDateFromUnix(unixTime) {
            let date = new Date(unixTime * 1000);
            return date;
        },
    },
    mounted () {
        var url = 'http://api.openweathermap.org/data/2.5/forecast?units=metric&lat=' + this.areadata[this.area].lat + '&lon='+ this.areadata[this.area].lon +'&lang=ja&appid=' + apikey;
        console.log(url);
        axios
        .get(url)
        .then(response => (this.info = response));
        console.log(this.info);
  }
}
</script>

<style>
.container {
    display: grid;
    margin: 10px;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
    gap: 20px;
    padding: 20px;
    background-color: rgb(49, 138, 197);
}

.item {
    border-style: groove; 
    border-color: rgb(117, 139, 199);
    text-align: center;
    color: black;
    background-color: rgb(255, 255, 255);
}

</style>