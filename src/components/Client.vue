<template>
  <div class="client">
    <v-row justify="center" justify-lg="start">
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
    grabUsers: function() {
      axios.get("https://jsonplaceholder.typicode.com/users").then(res => {
        this.clients = res.data;
      });
    }
  },
  beforeMount() {
    this.grabUsers();
  }
};
</script>
