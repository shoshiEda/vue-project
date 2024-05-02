<template>  
    <section class="watchers-index" :style="{ backgroundColor: watcher.backgroundColor }">
        <h3>Watcher:</h3>
        <p>{{watcher.name}}</p>
        <p>movies</p>
        <li v-for="show in watcher.shows" :key="show" >
            <p>{{show}}</p>
                </li>
        <button @click="back">back</button>
      </section>
</template>

<script>
import WatcherPreview from './WatcherPreview.vue'

export default {
    props: ['watcher'],
    methods:{
        back(){
            this.$emit('back')
        }
    }
}

</script>