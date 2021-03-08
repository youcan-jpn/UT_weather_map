<template>
    <div>
        <h2>{{ eng2kanji(area) }}</h2>
        <p>{{ info }}</p>
    </div>
</template>

<script>
const axios = require('axios')
export default {
    name: "WeatherInfo",
    props: {
        area: String
    },
    data () {
        return {
            info: null
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
        axios
        .get('http://api.openweathermap.org/data/2.5/forecast?lat=35.540712&lon=139.704723&lang=ja&appid={apikey}')
        .then(response => (this.info = response));
        console.log(this.info);
  }
}
</script>