<template>
  <div>
      <Counter :year="2022" :month="10" :date="1" :hour="10" :minutes="5" :milliseconds="5"/>
  </div>
</template>

<script>
import Counter from '../components/counter.vue'
  export default {
    components: {
      Counter
    },
    data: () => ({
      
    })
  }
</script>
