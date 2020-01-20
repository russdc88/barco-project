<template>
  <div class="client-post">
    <v-container>
      <v-row justify-lg="end" justify="end">
        <v-col lg="3" cols="3">
          <v-btn text to="/">
            <v-icon large>home</v-icon>
          </v-btn>
        </v-col>
      </v-row>
      <v-row justify="center">
        <v-col v-for="post in clientPosts" v-bind:key="post.id" cols="10">
          <v-card color="#01579B" dark>
            <v-card-title class="headline">{{post.title}}</v-card-title>

            <v-card-text>
              <div>{{post.body}}</div>
            </v-card-text>
            <v-expansion-panels>
              <v-expansion-panel>
                <v-expansion-panel-header color="#0277BD">Comments</v-expansion-panel-header>
                <v-expansion-panel-content color="#0277BD">
                  <Comments :postID="post.id" />
                </v-expansion-panel-content>
              </v-expansion-panel>
            </v-expansion-panels>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import Comments from "@/components/Comments.vue";
import axios from "axios";
export default {
  name: "posts",
  components: {
    Comments
  },
  data() {
    return {
      clientID: this.$route.params.id,
      clientPosts: []
    };
  },
  methods: {
    grabPost: function() {
      axios
        .get(
          "https://jsonplaceholder.typicode.com/posts?userId=" + this.clientID
        )
        .then(res => {
          this.clientPosts = res.data;
        });
    }
  },
  beforeMount() {
    this.grabPost();
  }
};
</script>