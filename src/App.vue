<template>
  <div id="app">
    <div id="test">
      <bar-chart :width=500 :option="options" :series="series" :title="title" :graph_id="graph_id"></bar-chart>
      <line-chart :width=500 :option="options" :series="series" :title="title" :graph_id="graph_id"></line-chart>
      <heatmap :width=500 :option="options" :series="series" :title="title" :graph_id="graph_id"></heatmap>
    </div>
  </div>
</template>

<script>
import BarChart from './components/graphs/BarChart'
import LineChart from './components/graphs/LineChart'
import Heatmap from './components/graphs/HeatChart'
export default {
  components: {
    BarChart, LineChart, Heatmap
  },
  data: function () {
    return {
      options: {
        chart: {
          id: 'vuechart-example'
        },
        xaxis: {
          categories: [91, 92, 93, 94, 95, 96, 97, 98]
        }
      },
      series: [{
        name: 'Metric1',
        data: [15, 23, 15, 9, 11, 3, 2, 15]
      },
      {
        name: 'Metric2',
        data: [15, 23, 15, 9, 11, 3, 2, 15]
      },
      {
        name: 'Metric3',
        data: [15, 23, 15, 9, 11, 3, 2, 15]
      },
      {
        name: 'Metric4',
        data: [15, 23, 15, 9, 11, 3, 2, 15]
      }],
      title: 'sample',
      graph_id: 'bar'
    }
  }
}
</script>
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
