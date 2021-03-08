<template>
    <div>
        <h2>{{ eng2kanji(area) }}</h2>
        <p>{{ info.data.list[0].main }}</p>
        <p>{{ info.data.list[2].main }}</p>
    </div>
</template>

<script>
const axios = require('axios')
const apikey = ''
// githubに載せないように注意

export default {
    name: "WeatherInfo",
    props: {
        area: String
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
        }
    },
    mounted () {
        var url = 'http://api.openweathermap.org/data/2.5/forecast?lat=' + this.areadata[this.area].lat + '&lon='+ this.areadata[this.area].lon +'&lang=ja&appid=' + apikey;
        console.log(url);
        axios
        .get(url)
        .then(response => (this.info = response));
        console.log(this.info);
  }
}
</script>