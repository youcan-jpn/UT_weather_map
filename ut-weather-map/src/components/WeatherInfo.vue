<template>
    <div>
        <h2>{{ eng2kanji(area) }}</h2>
    </div>
</template>

<script>
export default {
    name: "WeatherInfo",
    props: {
        area: String
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
    }
}
</script>