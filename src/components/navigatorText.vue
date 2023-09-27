<script setup>
const props = defineProps({
  text:String
})
</script>
<template>
  <p>{{ props.text }}</p>
</template>

<style scoped>
  p{
    color:#7a7a7a;
    font-size:0.9em;
    /* animation: sway 4s ease infinite */
  }
  @keyframes sway {
    0%,
    100% {
        transform: translateY(0px);
    }
    50% {
        transform: translateY(20px);
    }
  }
</style>