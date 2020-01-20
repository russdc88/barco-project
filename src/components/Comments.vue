<template>
  <div class="comments">
    <div class="new-comments" v-for="comment in comments" v-bind:key="comment.id">
      <h3>{{comment.name}}</h3>
      <p>"{{comment.body}}"</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "comments",
  props: {
    postID: Number
  },
  data() {
    return {
      comments: [],
      post_id: this.postID
    };
  },
  methods: {
    grabComments: function() {
      axios
        .get(
          "https://jsonplaceholder.typicode.com/comments?postId=" + this.post_id
        )
        .then(res => {
          this.comments = res.data;
        });
    }
  },
  beforeMount() {
    this.grabComments();
  }
};
</script>