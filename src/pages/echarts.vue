<template>
  <div>
    <chart
      id="test"
      :option="option"></chart>
  </div>
</template>

<script>
import chart from '../components/common/chart'
export default {
  name: 'echarts',
  components: {
    chart
  },
  data () {
    return {
      chartData: {
        xData: ['衬衫', '羊毛衫', '雪上衫', '裤子', '高', '袜子'],
        sData: [5, 20, 36, 10, 10, 70]
      },
      option: {
        title: {
          text: 'vue-Echarts'
        },
        legend: {
          data: ['销量']
        },
        xAxis: {
          data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
        },
        yAxis: [
          {
            type: 'value'
          }
        ],
        series: [
          {
            name: '销量',
            type: 'line',
            data: [5, 20, 36, 10, 10, 70]
          }
        ]
      }
    }
  },
  mounted () {
    this.refreshData()
  },
  methods: {
    refreshData () {
      let xData = this.chartData.xData
      let sData = this.chartData.sData
      for (let i = 0; i < xData.length; i++) {
        setTimeout(() => {
          this.option.xAxis.data.push(xData[i])
          this.option.series[0].data.push(sData[i])
        }, 1000 * i)
      }
    }
  }
}
</script>

<style lang="stylus">
</style>
