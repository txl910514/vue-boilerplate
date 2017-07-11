<template>
    <div class="map" ref="mapA">

    </div>
</template>

<script>
  const echarts = require('echarts');
  export default {
    name: 'map',
    data () {
      return {}
    },
    created () {
    },
    mounted () {
      this.initMap()
    },
    methods: {
      initMap () {
        const chartDom = this.$refs.mapA
        this.chart = echarts.init(chartDom)
        const startPoint = {
          x: 104.114129,
          y: 37.550339
        };
// 地图自定义样式
        const bmap = {
          center: [startPoint.x, startPoint.y],
          zoom: 5,
          roam: true,
          mapStyle: {
            styleJson: [{
              "featureType": "water",
              "elementType": "all",
              "stylers": {
                "color": "#044161"
              }
            }, {
              "featureType": "land",
              "elementType": "all",
              "stylers": {
                "color": "#004981"
              }
            }, {
              "featureType": "boundary",
              "elementType": "geometry",
              "stylers": {
                "color": "#064f85"
              }
            }, {
              "featureType": "railway",
              "elementType": "all",
              "stylers": {
                "visibility": "off"
              }
            }, {
              "featureType": "highway",
              "elementType": "geometry",
              "stylers": {
                "color": "#004981"
              }
            }, {
              "featureType": "highway",
              "elementType": "geometry.fill",
              "stylers": {
                "color": "#005b96",
                "lightness": 1
              }
            }, {
              "featureType": "highway",
              "elementType": "labels",
              "stylers": {
                "visibility": "off"
              }
            }, {
              "featureType": "arterial",
              "elementType": "geometry",
              "stylers": {
                "color": "#004981"
              }
            }, {
              "featureType": "arterial",
              "elementType": "geometry.fill",
              "stylers": {
                "color": "#00508b"
              }
            }, {
              "featureType": "poi",
              "elementType": "all",
              "stylers": {
                "visibility": "off"
              }
            }, {
              "featureType": "green",
              "elementType": "all",
              "stylers": {
                "color": "#056197",
                "visibility": "off"
              }
            }, {
              "featureType": "subway",
              "elementType": "all",
              "stylers": {
                "visibility": "off"
              }
            }, {
              "featureType": "manmade",
              "elementType": "all",
              "stylers": {
                "visibility": "off"
              }
            }, {
              "featureType": "local",
              "elementType": "all",
              "stylers": {
                "visibility": "off"
              }
            }, {
              "featureType": "arterial",
              "elementType": "labels",
              "stylers": {
                "visibility": "off"
              }
            }, {
              "featureType": "boundary",
              "elementType": "geometry.fill",
              "stylers": {
                "color": "#029fd4"
              }
            }, {
              "featureType": "building",
              "elementType": "all",
              "stylers": {
                "color": "#1a5787"
              }
            }, {
              "featureType": "label",
              "elementType": "all",
              "stylers": {
                "visibility": "off"
              }
            }]
          }
        }

       const option = {
          bmap: bmap,
          color: ['gold', 'aqua', 'lime'],
          backgroundColor: '#404a59',
          title: {
            text: '模拟迁徙+百度地图',
            subtext: 'data-visual.cn',
            sublink:'http://data-visual.cn',
            left: 'center',
            textStyle: {
              color: '#fff'
            }
          },
          tooltip: {
            trigger: 'item'
          },
          legend: {
            orient: 'vertical',
            top: 'bottom',
            left: 'right',
            data: ['北京 Top10', '上海 Top10', '广州 Top10'],
            textStyle: {
              color: '#fff'
            },
            selectedMode: 'single'
          },
          geo: {
            map: 'bmap',
            polyline: true,
            progressiveThreshold: 500,
            progressive: 200,
            label: {
              emphasis: {
                show: false
              }
            },
            roam: true,
            itemStyle: {
              normal: {
                areaColor: '#323c48',
                borderColor: '#404a59'
              },
              emphasis: {
                areaColor: '#2a333d'
              }
            }
          }
        };
        this.chart.setOption(option)
      }
    },
    components: {}
  }
</script>

<style lang="scss" rel="stylesheet/scss">
    #app {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        .map {
            height:calc(100vh - 60px);
        }
    }
</style>
