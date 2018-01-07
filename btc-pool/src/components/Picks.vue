<template>
  <div class="Picks">
		<ul>
			<li v-for="pick in picks" :key="pick.name">{{ pick.name }} {{ pick.price }} {{ pick.paid }}</li>
		</ul>
  </div>
</template>

<script>
import btcPicks from '../assets/picks.json'
export default {
  name: 'Picks',
  data: function () {
    return {
      picks: btcPicks
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
</style>
