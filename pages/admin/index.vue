<template >
	<div class="bg-grey-lighter text-grey-darker">
		<h1>Admin Dashboard</h1>
		
		<h2>Add New Events</h2>
		<hr />
		<hr />
		<h2>View Requests by Event</h2>
		
		
	</div>
</template>

<script>
import axios from 'axios'

/*export default {
  async asyncData () {
    let { data } = await axios.get(`http://localhost:3000/api/events`)
    return { data }
	}
}*/

export default {
	data () {
		return {
			email: ''
		}
	},
	created() {
		let eventData = axios.get(`http://localhost:3000/api/events`)
			.then(res => console.log(eventData))
			.catch(error => console.log(error))
	}
}

</script>

<style scoped>
	.all-events h3 {
		text-align: center;
	}
</style>
