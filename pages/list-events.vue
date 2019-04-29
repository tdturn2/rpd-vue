<template >
	<div class="container mx-auto bg-grey-lighter text-grey-darker p-5">
		<h1 class="pb-5">User Dashboard</h1>
		
		<div class="all-events flex mb-4">
			<div class="w-1/4 bg-grey p-5">
				<h3 class="text-3xl">Jan - Mar</h3>
				<div id="example"></div>
				
				
					<div class="event-listing" v-for="event in data">
						<div v-if="event.startDate <`2019-01-10`">
						<h4 class="pb-2">{{ event.eventName }}</h4>
						<p>{{ event.location }}</p>
						<p v-if="event.startDate === event.endDate">{{moment(event.startDate).format('MMM Do')}}</p>
						<p v-else>{{moment(event.startDate).format('MMM Do')}} - {{moment(event.endDate).format('MMM Do')}}</p>
						<!--<p>Formmatted date: {{moment(event.startDate).fromNow()}}</p> -->
						<!--<p>{{ reversedMessage }}</p> -->
					</div>

					</div>
				
			
			</div>
			<div class="w-1/4 bg-grey-light">
				<h3 class="text-3xl">Apr - Jun</h3>
			
			</div>
			<div class="w-1/4 bg-grey">
				<h3 class="text-3xl">Jul - Sep</h3>
			
			</div>
			<div class="w-1/4 bg-grey-light">
				<h3 class="text-3xl">Oct - Dec</h3>
			
			</div>
		</div>

		<hr />
		
		<pre>{{ data }}</pre>
		
	</div>
</template>

<script>
import axios from 'axios'

var moment = require('moment');

export default {
  async asyncData () {
		let { data } = await axios.get(`http://localhost:3000/api/events`)
    return { data }
	},
	methods: {
	  moment
	},
	computed: {
    // a computed getter
    reversedMessage: function () {
      // `this` points to the vm instance
			//return 'this.data.split('').reverse().join('')'
			return this.data[0];
    }
  }
	/*
	computed: {
		orderedDate: function () {
			return _.orderBy({data}, 'startDate')
		}
	}
	*/

	/*
	computed: {
		calculateDateRange() {
			var vm = this
			let startDate = vm.startDate;
			let endDate = moment(data.endDate).format('MMM Do')
			let eventDates = startDate + ' - ' + endDate;
			if (startDate == endDate) {
				eventDates = startDate;
			}
		}
	}
	*/
}


</script>

<style scoped>
	.all-events h3 {
		text-align: center;
	}
	.event-listing {
		border: 1px solid #000;
		border-radius: 10px;
		margin: 10px 0px;
		padding: 10px;
		background: #fff;
	}
</style>
