<template>
    <div id="test">
        <apexchart
            type="heatmap"
            :width="width"
            :options="options"
            :series="series" />
    </div>
</template>
<script>
export default {
  name: 'BarChart',
  props: {
    width: {
      type: Number,
      default: 500,
      required: false
    },
    series: {
      type: Array,
      required: false
    },
    option: {
      type: Object,
      required: false
    },
    title: {
      type: String,
      required: false
    },
    graph_id: {
      type: String,
      default: 'heatmap',
      required: false
    }
  },
  data: function () {
    return {
      options: {}
    }
  },
  mounted: function () {
    this.createOptions()
  },
  methods: {
    createOptions () {
      let setting = {
        chart: {
          events: {
            click: function (event, chartContext, config) {
              if (config.seriesIndex === -1 && config.dataPointIndex === -1) {
                console.log(event, chartContext, config)
              }
            },
            dataPointSelection: function (event, chartContext, config) {
              console.log(config.seriesIndex)
              console.log(config.dataPointIndex)
            },
            selection: function (chartContext, { xaxis, yaxis }) {
              console.log(xaxis, yaxis)
            }
          },
          id: this.graph_id,
          dataLabels: {
            enabled: false
          }
        },
        title: {
          text: this.title
        }
      }

      this.options = Object.assign(this.option, setting)
    }
  }
}

</script>
