<template>
  <div
    :id="id"
    :style="style"
    class="mall-chart ellipsis"
    style="height:378px"></div>
</template>

<script>
export default {
  name: 'Chart',
  data () {
    return {
      chart: ''
    }
  },
  props: {
    id: {
      type: String
    },
    width: {
      type: String,
      default: '100%'
    },
    height: {
      type: String,
      default: '300px'
    },
    option: {
      type: Object,
      default () {
        return {
          title: {
            text: ''
          },
          tooltip: {
            show: true,
            trigger: 'axis',
            axisPointer: {
              type: 'cross',
              crossStyle: {
                color: '#999'
              }
            },
            backgroundColor: 'RGBA(5, 21, 43, 0.8)',
            textStyle: {
              color: 'rgba(179, 193, 216, 1)',
              fontSize: 12
            },
            extraCssText: 'box-shadow:0px 0px 20px 0px rgba(1,125,255,0.49);',
            padding: [5, 10],
            formatter: function (params) {
              let res = '<div class="clearfix pb-10"><h3>新顾客量</h3>'
              for (let i = 0; i < params.length; i++) {
                res += '<p class="font-while-12 tooltip-p"><span class="fl tooltip-name">' + params[i].marker + params[i].seriesName + '</span><span class="fr font-spe-12">' + params[i].data + '</span></p>'
              }
              res += '</div>'
              return res
            }
          },
          legend: {
            data: ['主项目'],
            bottom: 0,
            textStyle: {
              color: 'rgba(179,193,216,1)'
            }
          },
          calculable: true,
          grid: {
            top: 37,
            left: '3%',
            right: '4%',
            bottom: '13%',
            containLabel: true
          },
          xAxis: [
            {
              name: '',
              type: 'category',
              boundaryGap: false,
              data: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31],
              axisLine: {
                lineStyle: {
                  color: '#b3c1d8'
                }
              }
            }
          ],
          yAxis: [
            {
              type: 'value',
              min: 0,
              max: 3500,
              splitLine: {
                show: true,
                lineStyle: {
                  color: 'rgba(22,62,115,1)',
                  width: 1,
                  type: 'solid'
                }
              },
              axisLine: {
                lineStyle: {
                  color: '#b3c1d8'
                }
              }
            }
          ],
          series: [
            {
              name: '主项目',
              data: ['1032', '683', '666', '637', '520', '261', '402', '762', '569', '588', '690', '628', '296', '238', '594', '619', '550', '592', '687', '340', '264', '689', '693', '578', '585', '709', '285', '243', '569', '600', '544'],
              type: 'line',
              compare: '300',
              symbol: 'circle',
              symbolSize: '5',
              showSymbol: 'false',
              lineStyle: { 'width': '1.5' },
              smooth: 'false',
              color: 'RGBA(13, 253, 242, 1)',
              projectLightColors: 'RGBA(13, 253, 242, .5)',
              areaStyle: {
                normal: {
                  color: {
                    type: 'linear',
                    x: 0,
                    y: 0,
                    x2: 0,
                    y2: 1,
                    colorStops: [{
                      offset: 0,
                      color: 'RGBA(13, 253, 242, .2)' // 0% 处的颜色
                    }, {
                      offset: 1,
                      color: 'transparent' // 100% 处的颜色
                    }],
                    globalCoord: false // 缺省为 false
                  }
                }
              }
            }
          ]
        }
      }
    }
  },
  computed: {
    style () {
      return {
        height: this.height,
        width: this.width
      }
    }
  },
  mounted () {
    this.init()
  },
  methods: {
    init () {
      this.chart = this.$echarts.init(document.getElementById(this.id))
      this.chart.setOption(this.option)
      window.addEventListener('resize', this.chart.resize)
    }
  },
  watch: { // 数据自动刷新
    option: {
      handler (newVal, oldVal) {
        if (this.chart) {
          if (newVal) {
            this.chart.setOption(newVal)
          } else {
            this.chart.setOption(oldVal)
          }
        } else {
          this.init()
        }
      },
      deep: true
    }
  }
}
</script>

<style lang="stylus">
</style>
