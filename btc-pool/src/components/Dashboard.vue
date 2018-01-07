<template>
  <div class="Dashboard">
		<chart></chart>
		<picks></picks>
  </div>
</template>

<script>
import Chart from './Chart.vue'
import Picks from './Picks.vue'
export default {
  name: 'Dashboard',
  data: function () {
    return {
      msg: 'Dashboard works!'
    }
  },
  components: {
    'chart': Chart,
    'picks': Picks
  }
}
</script>