<template>
  <div>
    <!-- here you can assign when the end od count down should be! -->
      <Counter :year="2022" :month="10" :day="1" :hours="10" :minutes="5" :seconds="5" :milliseconds="5"/>
  </div>
</template>

<script>
import Counter from '../components/counter.vue'
  export default {
    components: {
      Counter
    },
  }
</script>
