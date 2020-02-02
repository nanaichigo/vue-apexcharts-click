<template>
    <div id="test">
        <apexchart
            type="line"
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
      default: 'line-cahrt',
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
            // click: function (event, chartContext, config) {
            //   console.log(config.seriesIndex)
            //   console.log(config.dataPointIndex)
            //   console.log(config)
            //   console.log(config.series[config.seriesIndex].name)
            // },
            dataPointSelection: function (event, chartContext, config) {
              console.log(config.seriesIndex)
              console.log(config.dataPointIndex)
            }
          },
          id: this.graph_id
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
