<template>
  <v-app>
		<Navbar/>
		<Client/>
  </v-app>
</template>

<script>
import Client from './components/Client';
import Navbar from './components/Navbar';

export default {
  name: 'App',

  components: {
		Client,
		Navbar
  },

  data: () => ({
    //
  }),
};
</script>
