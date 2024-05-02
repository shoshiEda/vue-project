import { default } from '../App.vue';

<template>
      <div @click="changeColor" :class="dynClass + ' season'">
        <h2>{{ month }}({{ season }})</h2>
        <img :src="'/img/' + season + '.png'" />
        <div class="clock">{{ currentTime }}</div>
      </div>
  </template>
  
  <script>

  export default {
    data() {
      return {
        dynClass: 'light',
        clock: { hour: '', minutes: '', seconds: '' },
        month: '',
        day: '',
        season: '',
        intervalId: null
      }
    },
    mounted() {
      this.updateTime();
      this.intervalId = setInterval(this.updateTime, 1000);
    },
    beforeDestroy() {
      clearInterval(this.intervalId);
    },
    methods: {
      updateTime() {
        const now = new Date();
        this.clock = {
          hour: this.padZero(now.getHours()),
          minutes: this.padZero(now.getMinutes()),
          seconds: this.padZero(now.getSeconds())
        };
        this.month = this.getMonthName(now.getMonth());
        this.day = now.getDate();
        this.season = this.getSeason(now.getMonth());
      },
      padZero(num) {
        return num < 10 ? '0' + num : num;
      },
      getMonthName(month) {
        const months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'];
        return months[month];
      },
      getSeason(month) {
        const seasons = ['winter', 'spring', 'summer', 'autumn'];
        if (month >= 2 && month <= 4) return seasons[1];
        else if (month >= 5 && month <= 7) return seasons[2];
        else if (month >= 8 && month <= 10) return seasons[3];
        else return seasons[0];
      },
      changeColor() {
        this.dynClass = this.dynClass==='light'? 'dark' :'light'
        console.log(this.dynClass)
      },
      
    },
    computed: {
      currentTime() {
        return `${this.clock.hour}:${this.clock.minutes}:${this.clock.seconds}`;
      }
    }
  }
  </script>
  
  <style scoped>
  
  .season {
    padding: 1.5rem;
    margin: 1rem;
    border-radius: 10px;
    cursor: pointer;
    text-align: center;
    border: solid 3px blue;
    display: inline-block;
    margin-inline-start:50%;
    margin-block:1rem;
    transform:translate(-50%);

  }

  .dark{
    background-color: blue;
    color: white;
  }

  .light{
    background-color: white;
    color:black;
  }
  
  .clock {
    font-size: 24px;
    margin-top: 10px;
  }
  
  </style>
  
