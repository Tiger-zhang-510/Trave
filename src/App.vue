<template>
  <div id="app">
      <keep-alive exclude="Detail"><!--除了detail组建以外的组建都缓存-->
      <router-view/>
    </keep-alive>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>

</style>
