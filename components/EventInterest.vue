<template>
  <div>
		<input type="radio" v-model="color" value="0">red
  <input type="radio" v-model="color" value="1">blue
  <input type="radio" v-model="color" value="2">yellow
	</div>
</template>


<script>
export default {
  name: 'EventInterest',
  
	data: {
		options: {
      '0': 'Female',
      '1': 'Male'
     },
     gender: null
  }		

}

</script>

<style scoped>

</style>


