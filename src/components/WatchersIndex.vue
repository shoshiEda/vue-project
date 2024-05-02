<template>  
      <section class="watchers-index">
        <h3>Watchers:</h3>
            <button @click="onAddWatcher">Add a Watcher</button>
            <WatcherList @remove="removeWatcher" :watchers="watchers" />
        </section>
</template>

<script>
  import WatcherList from './WatcherList.vue'

export default{
  data() {
        return {
            watchers: [
                { id: 'p101', name: 'Charlie', shows: ['fjfnd','bfrhjbfr']},
                { id: 'p102', name: 'Bobbi', shows: ['fjfdfdfnd','bfrhjbfr'] },
                { id: 'p103', name: 'Rorri', shows: ['fnd','bfrhjbfr'] },
            ]
        }
    },
    methods: {
      removeWatcher(watcherId) {
        console.log('hi')
            const idx = this.watchers.findIndex(watcher => watcher.id === watcherId)
            this.watchers.splice(idx, 1)
        },
        onAddWatcher() {
            const now = Date.now()
            const name=prompt('what is your name?')
            const watcher =  {
                id: 'p' + now % 1000,
                name,
                shows:[]
            }
            this.watchers.unshift(watcher)
        }
    },
    components: {
        WatcherList,
    }
}

</script>