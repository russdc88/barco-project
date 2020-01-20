<template>
	<div class="client">
		<v-row>
			<v-col
			v-for="client in clients"
			v-bind:key="client.id"
			xl='2'
			lg='3'
			md='4'
			sm='6'
			xs='12'>
				<v-card
				color="#385F73"
				dark
				>
					<v-card-title class="headline">{{client.name}}</v-card-title>
					<v-card-actions>
						<v-btn 
						text
						:to="'/post/' + client.id "
						>See Post</v-btn>
					</v-card-actions>
					</v-card>
			</v-col>
		</v-row>
	</div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Client',
	data () {
		return {
			clients:[]
		}
	},
	methods: {
		grabUsers:function () {
			axios.get('https://jsonplaceholder.typicode.com/users').then(res => {
			this.clients = res.data
			console.log(this.clients)
			})
		}
	},
		beforeMount() {
		this.grabUsers()
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
