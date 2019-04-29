<template >
	<div class="admin-post-event bg-grey-lighter text-grey-darker ">
		

		<section class="new-post-form">
			<div class="container mx-auto">
				<h1>Add Post Event</h1>
			<form @submit.prevent="onSave">
				<AppControlInput v-model="editedEvent.eventName">Event Name</AppControlInput>
				<AppControlInput v-model="editedEvent.startDate">Start Date</AppControlInput>				
				<AppControlInput v-model="editedEvent.endDate">End Date</AppControlInput>			
				<AppControlInput v-model="editedEvent.description">Description</AppControlInput>		
				<AppControlInput v-model="editedEvent.location">Location</AppControlInput>				
				<AppControlInput v-model="editedEvent.code">Code</AppControlInput>			
				
				<AppButton type="submit">Save</AppButton>		
				<AppButton
									type="button"
									style="margin-left: 10px"
									btn-style="cancel"
									@click="onCancel">Cancel</AppButton>
			</form>
			</div>
		</section>	
		
	</div>
</template>

<script>
import AppControlInput from '@/components/UI/AppControlInput'
import AppButton from '@/components/UI/AppButton'
import axios from 'axios'

/*export default {
  async asyncData () {
    let { data } = await axios.get(`http://localhost:3000/api/events`)
    return { data }
	}
}*/

export default {
	components: {
		AppControlInput,
		AppButton
	},
	
	data () {
		return {
			editedEvent: {
				eventName: this.eventName,
				startDate: this.startDate,
				endDate: this.endDate,
				description: this.description,
				location: this.description,
				code: this.code
			}
		}
	},
	methods: {
		onSave() {
			// Save post	
			// console.log(this.editedPost);
			//this.$emit('submit', this.editedPost)
			axios.post('http://localhost:3000/api/events', this.editedEvent)
			 .then(result => console.log(result))
			 .catch(e => console.log(e));
			 
		},
		onCancel() {
			// Navigate back
			this.$router.push('/admin');
		}
	}
}

</script>

<style scoped>
	.all-events h3 {
		text-align: center;
	}
</style>
