<template>
      <h3>Show coords:</h3>
      <p>x:{{x}} ,y:{{y}}</p>
      
</template>

<script>

  export default {
    data() {
      return {
       x:0,
       y:0
      }
    },
    mounted() {
    window.addEventListener("mousemove", this.handleMouseMove);
  },
  beforeDestroy() {
    window.removeEventListener("mousemove", this.handleMouseMove);
  },
  methods: {
    handleMouseMove(event) {
      this.x = event.clientX;
      this.y = event.clientY;
    }
  }
}
  </script>