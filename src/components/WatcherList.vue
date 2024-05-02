<template>  
    <section class="watcher-list">
            <ul>
                <li v-for="watcher in watchers" :key="watcher.id" :style="{ backgroundColor: randomColor() }">
                    <WatcherPreview :watcher="watcher" />
                    <button @click="onRemoveWatcher(watcher.id)">x</button>
                </li>
            </ul>
        </section>
</template>

<script>
import WatcherPreview from './WatcherPreview.vue'

export default {
    props: ['watchers'],
    
    methods: {
        onRemoveWatcher(watcherId) {
            this.$emit('remove', watcherId)
        },    
        randomColor() {
            return '#' + Math.floor(Math.random() * 16777215).toString(16);
        }

    },
    created() {
    
    this.watchers.forEach(watcher => {
      watcher.backgroundColor = this.randomColor();
    })
},
    components: {
        WatcherPreview,
    }
}

</script>