<template>  
    <article class="watcher-preview" >
            <h2>{{watcher.name}}</h2>
            <img src="../assets/img/watcher.webp"/>
        </article>
</template>

<script>

export default {
    props: ['watcher'],
}

</script>