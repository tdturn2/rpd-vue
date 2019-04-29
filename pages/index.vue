<template >
	<div class="container mx-auto bg-grey-lighter text-grey-darker p-5">
		<h1 class="pb-5">User Dashboard</h1>
		<h2>To do</h2>
		<ul class="m-5">
			<li>Add survey (Very Interested, Available, If Needed, No)</li>


		</ul>
		<!--
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

						<!--
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
-->
		<hr />

		<table class="event-listing1">
			<thead>
				<tr class="text-center bg-grey-darkest text-white font-bold">
					<td>Date</td>
					<td>Event Name</td>
					<td>Location</td>
					<td>Interest</td>
				</tr>
			</thead>
			<tbody>
			<tr class="m-5" v-for="event in data">
					<td v-if="event.startDate === event.endDate">{{moment(event.startDate).format('MMM Do')}}</td>
					<td v-else>{{moment(event.startDate).format('MMM Do')}} - {{moment(event.endDate).format('MMM Do')}}</td>
					<td>{{ event.eventName }}</td>
					<td>{{ event.location }}</td>
					<td>
						<div class="radio-interest">
							<input type="radio" :name="'interest_' + event.eventName" v-bind:value="4" @change="changeInterest(event.eventName)"><label>Very Interested</label>
							<input type="radio" :name="'interest_' + event.eventName" v-bind:value="3"><label>Available</label>
							<input type="radio" :name="'interest_' + event.eventName" v-bind:value="2"><label>If Needed</label>
							<input type="radio" :name="'interest_' + event.eventName" v-bind:value="1"><label>Not Available</label>
						</div>
					</td>
				</tr>
							<!--
						<td v-if="event.startDate === event.endDate">{{moment(event.startDate).format('MMM Do')}}</td>
						<td v-else>{{moment(event.startDate).format('MMM Do')}} - {{moment(event.endDate).format('MMM Do')}}</td>
						<!--<p>Formmatted date: {{moment(event.startDate).fromNow()}}</p> -->
						<!--<p>{{ reversedMessage }}</p> -->
			</tbody>
			</table>
			<p>Name: {{jwtData.sub}} </p>
		
	<!--	<pre>{{ data }}</pre> -->
		
	</div>
</template>

<script>
import axios from 'axios'
var moment = require('moment');
import EventInterest from '@/components/EventInterest'


export default {
	middleware: ['check-auth', 'auth', 'getUserData'],
  async asyncData () {
		let { data } = await axios.get(`http://localhost:3000/api/events`)
    return { data }
	},
	data () {
		return {
			picked: null
		}
	},
	components: {
		EventInterest
	},

	methods: {
		moment,
		changeInterest(avar) {
			const tempUserID = '5cb7cd23c8ff4a231c750de4';

			// Check to see if Interest is set for that event (GET)

			axios.get(`http://localhost:3000/api/events`)
				.then(response => {
					// JSON responses are automatically parsed.
					this.posts = response.data
				})
				.catch(e => {
					this.errors.push(e)
				})

			// If yes, do a put by ID and interest level
			// If not, do a post by ID and interest level


			//console.log(localStorage.getItem("token") + ' ' + avar);
		}
	},
	computed: {
    // a computed getter
    reversedMessage: function () {
      // `this` points to the vm instance
			//return 'this.data.split('').reverse().join('')'
			return this.data[0];
		},
		
    // this.jwtData will update whenever this.jwt changes.
    jwtData() {
      // JWT's are two base64-encoded JSON objects and a trailing signature
      // joined by periods. The middle section is the data payload.
      if (this.jwt) return JSON.parse(atob(this.jwt.split('.')[1]));
      return {};
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
	.event-listing1 {
		border: 1px solid #eee;
		background: #fff;
	}
	.event-listing1 tr td {
		padding: 15px;
	}
	.event-listing1 tbody tr {
		border-bottom: 1px solid rgb(233, 233, 233);
	}

	.radio-interest label {
		padding: 0 4px;
	}
</style>
