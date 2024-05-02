import { default } from '../App.vue';

<template>
      <div class="count-down">
        <span>{{ counter.minutes }}</span>:<span :style="textStyle">{{ counter.seconds }}</span>
      </div>
  </template>
  
  <script>

export default {
  data() {
    return {
      dynClass: '',
      counter: { hour: '', minutes: '', seconds: '' },
      intervalId: null,
      endTime : Date.now() + 1000 * 60
    };
  },
  mounted() {
    this.updateTime();
    this.intervalId = setInterval(this.updateTime, 1000);
  },
  methods: {
    updateTime() {
      const remainingTime = this.endTime - Date.now();
      if (remainingTime <= 0) {
        clearInterval(this.intervalId);
        return;
      }
      if (remainingTime <= 10000) {
        this.dynClass='red'
      }
      const minutes = this.padZero(Math.floor((remainingTime % (1000 * 60 * 60)) / (1000 * 60)));
      const seconds = this.padZero(Math.floor((remainingTime % (1000 * 60)) / 1000));
      this.counter = { minutes, seconds };
    },
    padZero(num) {
        return num < 10 ? '0' + num : num;
      },
  },
 
  computed: {
  currentTime() {
    return `${this.counter.minutes}:${this.counter.seconds}`;
  },
  textStyle() {
    return {
      color: this.dynClass === 'red' ? 'red' : 'black',
    }
  },
},
}


  </script>
  
  <style scoped>

  .count-down{
    border: solid 2px black;
    display: inline-block;
    margin-inline-start:50%;
    transform:translate(-50%);
    margin-block:1rem;
    border-radius:0.5rem;
   padding:0.5rem;
    text-align:center;
  }
  span{
    font-weight:bold;
  }

  .red{
    color:red;
  }
 
  
  </style>
  
