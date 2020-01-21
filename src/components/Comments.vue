// This is the comments component that creates the template for all the comments for a specific post
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
	// created a prop for postID so I can call in the post component
  props: {
    postID: Number
  },
  data() {
    return {
			comments: [],
			// creating data to grab the postid from the prop so I can use it in the API call
      post_id: this.postID
    };
  },
  methods: {
		// grabbing comments associated with the post id
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