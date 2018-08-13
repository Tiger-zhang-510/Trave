<template>
  <div id="app">
      <keep-alive exclude="Detail"><!--除了detail组建以外的组建都缓存-->
      <router-view/>
    </keep-alive>
  </div>
</template>

<script>
import jsonp from 'common/js/jsonp'
export default {
  name: 'App',
  created: function() {
    getRecommend().then((res) => {
      console.log(res.data)
    })
  }
}
function getRecommend() {
  const url = 'https://touch.piao.qunar.com/touch/list.json'
  const data = {}
  const options = {
    param: 'jsonpCallback'
  }
  return jsonp(url, data, options)
}
</script>

<style>

</style>
