<template>
  <div class="Chart">
		<h1>{{ msg }}</h1>
		<svg width="500" height="270">
    <g style="transform: translate(0, 10px)">
      <path :d="line" />
    </g>
  </svg>
  </div>
</template>

<script>
import * as d3 from "d3";
export default {
  name: "Chart",
  data: function() {
    return {
			msg: "Chart works!",
			data: [13354, 14709, 15155, 15160, 16917, 16900],
      line: '',
    };
  },
  mounted() {
		var svg = d3.select("svg");
		var g = d3.select("g");
		var width = +svg.attr("width");
		var height = +svg.attr("height");

		const xScale = d3.scaleTime()
			.range([0, width])
			.domain(d3.extent(this.data, (d, i) => i));
		const yScale = d3.scaleLinear()
			.range([height, 0])
			.domain([d3.min(this.data, d => d), d3.max(this.data, d => d)]);

		var xAxis = d3.axisBottom().scale(xScale);
		var yAxis = d3.axisLeft().scale(yScale);

		g.append("g")
      .call(yAxis)
    	.append("text")
      .attr("fill", "#FFFFFF")
      .attr("transform", "rotate(-90)")
      .attr("y", 6)
      .attr("dy", "0.71em")
      .attr("text-anchor", "end")
			.text("Price ($)");

		const path = d3.line()
			.x((d, i) => xScale(i))
			.y(d => yScale(d));
		this.line = path(this.data);
  }
};
</script>

<style scoped>
svg {
	padding:10px;
	border: solid 0.5px gray;
  margin: 25px;
}
path {
  fill: none;
  stroke: #76BF8A;
  stroke-width: 3px;
}
</style>