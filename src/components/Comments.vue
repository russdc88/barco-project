<template>
		<div class="comments">
			<div class="new-comments" v-for="comment in comments"
			v-bind:key="comment.id">
			<v-list-item>
				<v-list-item-content>
					<v-list-item-header>
						{{comment.name}}
					</v-list-item-header>
					<v-list-item-subtitle>
						{{comment.body}}
					</v-list-item-subtitle>
				</v-list-item-content>
			</v-list-item>

			</div>
		</div>
</template>

<script>
import axios from 'axios'
export default {
	name: 'comments',
	props: {
		postID: Number
	},
	data () {
		return {
			comments: [],
			post_id: this.postID
		}
	},
	methods: {
		grabComments: function (){
			console.log(this.post_id)
			axios.get('https://jsonplaceholder.typicode.com/comments?postId=' + this.post_id).then(res => {
			this.comments = res.data
			console.log(this.comments)
			})
		}
	},
	mounted() {
		this.grabComments()
	}
}
</script>