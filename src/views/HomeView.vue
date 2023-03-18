<template>
  <div class="home">
    <img alt="Smiley" src="../assets/pexels-count-chris-8588947.jpg" style="height: 25rem; width: 25rem; border-radius: 12.5rem;">
    <HelloWorld msg="Welcome to Olubukola's Counter"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  }
}
</script>


