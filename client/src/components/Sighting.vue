<template lang="html">
  <div class="sighting">
    <h2>{{ sighting.species }}</h2>
    <p>{{ sighting.location }} on {{ sighting.date|formatDate }}</p>

    <button>Delete Sighting</button>
  </div>
</template>

<script>

import { eventBus } from '@/main.js'
import SightingService from '@/services/SightingService.js'

export default {
  name: 'sighting',
  props: ['sighting'],
  filters: {
    formatDate(value) {
      return new Date(value).toLocaleString().substring(0, 10);
    }
  },

}
</script>

<style lang="css" scoped>
.sighting {
	width: 30%;
	background: rgba(255, 255, 255, 0.7);
	margin-bottom: 20px;
	padding: 25px;
}

button {
	color: #fff;
	border: none;
	font-size: 18px;
	padding: 10px;
	margin-top: 10px;
	background: #F55536;
}
</style>
