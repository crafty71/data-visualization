<template>
  <div class="home">
    <top-view />
    <sales-view />
    <bottom-view />
    <map-view />
  </div>
</template>

<script>
import TopView from '../components/TopView'
import SalesView from '../components/SalesView'
import BottomView from '../components/BottomView'
import MapView from '../components/MapView'
import { wordcloud, screenData, mapScatter } from '../api'
import reportData2 from './mockdata'
import wordCloud2 from './wordCloud'

export default {
  name: 'Home',
  components: {
    TopView,
    SalesView,
    BottomView,
    MapView
  },
  data() {
    return {
      reportData: null,
      wordCloud: null,
      mapData: null,
      reportData1: reportData2,
      wordCloud1: wordCloud2
    }
  },
  methods: {
    getReportData() {
      return this.reportData
    },
    getWordCloud() {
      return this.wordCloud
    },
    getMapData() {
      return this.mapData
    }
  },
  provide() {
    return {
      getReportData: this.getReportData,
      getWordCloud: this.getWordCloud,
      getMapData: this.getMapData
    }
  },
  mounted() {
    screenData().then((data) => {
      this.reportData = data
      // this.reportData = this.reportData1.reportData
      // console.log(this.reportData)
    })
    wordcloud().then((data) => {
      this.wordCloud = data
      // this.wordCloud = this.wordCloud1.wordCloud
    })
    mapScatter().then((data) => {
      this.mapData = data
    })
  }
}
</script>

<style>
.home {
  width: 100%;
  padding: 20px;
  background: #eee;
  box-sizing: border-box;
}
</style>
