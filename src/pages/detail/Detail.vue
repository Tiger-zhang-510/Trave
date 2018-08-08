<template>
 <div>
     <detail-banner 
       :sightName="sightName"
       :bannerImg="bannerImg"
       :bannerImgs="gallaryImgs"
     ></detail-banner>
     <detail-header></detail-header>
     <div class="content"></div>
 </div>
</template>

<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
 export default {
   name: 'Detail',
   data () {
     return {
         sightName: '',
         bannerImg: '',
         gallaryImgs: [],
         list: [],
     }
   },
   components: {
       DetailBanner,
       DetailHeader,
   },
   methods:{
       getDetailInfo() {
           this.$axios.get('/api/detail.json',{
               params: {
                   id: this.$route.params.id
               }
           })
             .then((res) =>{
               res = res.data;
               if(res.ret && res.data) {
                   const data = res.data;
                   this.sightName = data.sightName;
                   this.bannerImg = data.bannerImg;
                   this.gallaryImgs = data.gallaryImgs;
                   this.list = data.categoryList

               }
           })
       }
   },
   mounted() {
       this.getDetailInfo()
   }
 }
</script>

<style scoped>
.content{
    height: 50rem 
}
</style>
