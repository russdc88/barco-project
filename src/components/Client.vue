// This is the client component where I generate all the clients from the Json Placeholder API
<template>
  <div class="client">
    <v-row justify="center" justify-lg="start">
			<!-- generating into list of cards with their name and link to their osts -->
      <v-col
        v-for="client in clients"
        v-bind:key="client.id"
        xl="2"
        lg="3"
        md="4"
        sm="6"
        xs="12"
        cols="11"
      >
        <v-card color="#01579B" dark>
          <v-card-title class="headline">{{client.name}}</v-card-title>
          <v-card-actions>
						<!-- creating a route paramenter to call in the Post component -->
            <v-btn text :to="'/post/' + client.id ">See Post</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Client",
  data() {
    return {
      clients: []
    };
  },
  methods: {
		// api call to get all the client data from API
    grabUsers: function() {
      axios.get("https://jsonplaceholder.typicode.com/users").then(res => {
        this.clients = res.data;
      });
    }
	},
	// want to call method before the component mounts
  beforeMount() {
    this.grabUsers();
  }
};
</script>
