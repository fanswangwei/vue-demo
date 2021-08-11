<template>
  <div class="home">
    <organizeMap msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import organizeMap from '@/components/organizeMap.vue'

export default {
  name: 'Home',
  components: {
    organizeMap
  }
}
</script>
