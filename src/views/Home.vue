<template>
  <div class="home">
    <Client/>
  </div>
</template>

<script>
// @ is an alias to /src
import Client from '@/components/Client.vue'

export default {
  name: 'home',
  components: {
    Client
  }
}
</script>
