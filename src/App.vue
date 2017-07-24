<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
import Quote from '@/components/Quote'

export default {
  name: 'app',
  components: {
    Quote
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
  margin-top: 60px;
}
h4 {
  margin-top: 30px;
  color: #337ab7;
  margin-bottom: 50px;
}
h2 {
  color: rgba(128, 128, 128, 0.52);
}
h2 .label {
  font-size: 12px;
  margin-left: 10px;
}
.glyphicon {
  color: rgba(76, 203, 83, 0.51);
  text-align: center;
  display: inline-block;
    padding-right: 8px;
}
.quote-title {
  display: inline-block;
  text-transform: uppercase;
  font-weight: bold;
  font-size: 18px;
}
#get_quote_btn {
  float: right;
}
#tweet_quote_btn {
  float: left;
  padding: 6px 30px;
}
</style>
