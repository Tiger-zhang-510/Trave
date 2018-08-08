<template>
 <div>
     <div class="banner" @click="handleBannerClick">
         <img class="banner-img" :src="bannerImg" alt="图片加载中">
         <div class="banner-info">
             <div class="banner-title">
                 {{this.sightName}}
             </div>
             <span class="banner-number"></span>
             <span class="iconfont icon-moreunfold">{{this.bannerImgs.length}}</span>
         </div>
     </div>
     <common-gallary
       :imgs="bannerImgs"
       v-show="showGallary"
       @close="handleGallaryClick"
     ></common-gallary>
 </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
 export default {
   name: 'DetailBanner',
   props: {
       sightName: String,
       bannerImg: String,
       bannerImgs: Array,
   },
   data () {
     return {
         showGallary: false, 
     }
   },
   methods: {
       handleBannerClick() {
           this.showGallary = true
       },
       handleGallaryClick() {
           this.showGallary = false
       }
   },
   components: {
       CommonGallary,
   }
 }
</script>

<style lang="stylus" scoped>
.banner 
  overflow: hidden 
  position: relative 
  height:0  
  padding-bottom: 55%
  .banner-img 
    width: 100% 
  .banner-info 
    display: flex 
    position: absolute 
    left: 0 
    right: 0 
    bottom: 0 
    line-height: .6rem 
    color: #fff 
    background-image: linear-gradient(rgba(0,0,0,0),rgba(0,0,0,.8))
    .banner-title 
      flex: 1 
      font-size: .32rem 
      paddng: 0 .2rem 
    .banner-numner 
      padding: 0 .4rem 
      margin-top: .2rem 
      height: .4rem 
      line-height: .4rem 
      border-radius: .2rem 
      font-size: .24rem    
</style>
