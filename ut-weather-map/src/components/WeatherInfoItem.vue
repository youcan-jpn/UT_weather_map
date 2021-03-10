<template>
    <div>
        {{ month }}/{{ date }} <span class="hour">{{ hour }}時</span><br />
        <img :src="iconPath" height="100" alt="weatherIcon" /><br />
        予想気温:<span class="temperature">{{ forecastedTemp }}&deg;C</span>
    </div>
</template>

<script>
export default {
    props: {
        item: Object
    },
    computed: {
        rawdate: function() {
            let rawdate = new Date(this.item.dt * 1000);
            return rawdate;
        },
        month: function() {
            return this.rawdate.getMonth() + 1;
        },
        date: function() {
            return this.rawdate.getDate();
        },
        hour: function() {
            return this.rawdate.getHours();
        },
        forecastedTemp: function() {
            return Math.round(this.item.main.temp);
        },
        iconPath: function() {
            return require('../../public/' + this.item.weather[0].icon + '.png')
        }
    }
}
</script>

<style>
.temperature {
    color: rgb(20, 16, 16);
    font-size: 1.4em;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}
.hour {
    font-size: 1.6em;
}
</style>