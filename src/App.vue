<script>
import Clock from './components/Clock.vue'
import CountDown from './components/CountDown.vue'
import WatchersIndex from './components/WatchersIndex.vue'
import ShowCords from './components/ShowCords.vue'


export default {
  data(){
    return {
            router: 'Clock',
        }
  },

  components: {
    Clock,
    CountDown,
    WatchersIndex,
    ShowCords,
  }
}
</script>

<template>
  <header class="header">
    <h3>Hello Vue</h3>
    <nav>
      <button @click="router = 'Clock'">Clock</button>
      <button @click="router = 'CountDown'">CountDown</button>
      <button @click="router = 'WatchersIndex'">Watchers Index</button>
      <button @click="router = 'ShowCords'">Show cords</button>
    </nav>
  </header>

  <main>
    <Clock v-if="router === 'Clock'"/>
    <CountDown v-else-if="router === 'CountDown'" />
    <WatchersIndex v-else-if="router === 'WatchersIndex'" />
    <ShowCords v-else-if="router === 'ShowCords'"  />
  </main>
</template>

<style scoped>
.header{
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: green;
  padding: 0.5rem;
  border-radius: 0.5rem;
}

h3{
  color:yellow;
  font-weight: bold;
}

button{
  border: none;
  background-color: transparent;
  color:lightgoldenrodyellow;
}

button:hover{
  cursor: pointer;
  color:yellow;
}

</style>
