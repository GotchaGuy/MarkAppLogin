<template>
  <div class="home">
    <logIn/>
  </div>
</template>

<script>
// @ is an alias to /src
import logIn from '@/components/logIn.vue'

export default {
  name: 'home',
  components: {
    logIn
  }
}
</script>
