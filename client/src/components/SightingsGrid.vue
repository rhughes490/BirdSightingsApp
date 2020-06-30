<template lang="html">
	<div id="sightingsGrid">
		<sighting v-for="sighting in sightings" :sighting="sighting" />
	</div>
</template>

<script>
import { eventBus } from '@/main.js';
import SightingService from '@/services/SightingService.js';
import Sighting from './Sighting';

export default {
	name: 'sightings-grid',
	data(){
		return {
			sightings: []
		};
	},
	mounted(){
		SightingService.getSightings()
		.then(sightings => this.sightings = sightings);

		eventBus.$on('sighting-added', (sighting) => {
			this.sightings.push(sighting)
		})
	},
	components: {
		'sighting': Sighting
	}
	
}
</script>

<style lang="css" scoped>
#sightingsGrid {
	display: flex;
	flex-wrap: wrap;
	justify-content: space-evenly;
}

h2 {
	padding: 0;
	margin: 0;
}
</style>
