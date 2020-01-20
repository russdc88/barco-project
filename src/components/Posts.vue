<template>
	<div class="client-post">
		<v-row>
			<v-col
			v-for="post in clientPosts"
			v-bind:key="post.id"
			xl='6'
			lg='6'
			md='6'
			sm='6'
			xs='12'>
				<v-card
				color="#385F73"
				dark
				>
					<v-card-title class="headline">{{post.title}}</v-card-title>

					<v-card-text>
						<div>
							{{post.body}}
						</div>
					</v-card-text>
					<v-expansion-panels>
						<v-expansion-panel>
							<v-expansion-panel-header>
								Comments
							</v-expansion-panel-header>
							<v-expansion-panel-content>
								<Comments :postID="post.id"/>
							</v-expansion-panel-content>
						</v-expansion-panel>
					</v-expansion-panels>
					</v-card>
			</v-col>
		</v-row>
	</div>
</template>

<script>
import Comments from '@/components/Comments.vue'
import axios from 'axios'
export default {
	name: "posts",
	components: {
		Comments
	},
	data () {
		return {
			clientID:this.$route.params.id,
			clientPosts:[]
		}
	},
	methods: {
		grabPost: function() {
			
			axios.get( 'https://jsonplaceholder.typicode.com/posts?userId=' + this.clientID).then(res => {
				this.clientPosts = res.data
				console.log(this.clientPosts)
			})
		}
	},
	beforeMount() {
		this.grabPost()
	}
}
</script>