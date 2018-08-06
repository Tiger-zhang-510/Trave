<template>
<div>
    <div class="recommend-title">
        <img class="img" src="https://imgs.qunarzz.com/piao/fusion/1711/16/bfbb9874e8f11402.png" alt="图片加载中...">
        <span class="hot">本周热门榜单</span>
        <a class="all" href="http://touch.piao.qunar.com/touch/weekHotSales.htm?cityName=西安">全部榜单 ></a>
    </div>
    <ul class="hot-list">
        <swiper>
            <swiper-slide v-for="(page,index) in pages" :key="index">
                <li class="hot-item" 
                    v-for="item in page"
                    :key="item.id"
                    >
                   <a class="mp-fulllink" href="" >
                       <div class="mp-hotsale-imgcon image-ready">
                           <img :src="item.imgUrl" alt="秦始皇陵博物院（兵马俑）">
                       </div>
                       <div class="mp-hotsale-sight mp-ellipsis">{{item.desc}}</div>
                       <div class="mp-hotsale-price">
                           <span class="mpg-price">¥<em class="mpg-price-num">{{item.price}}</em></span>起
                       </div>
                    </a>   
                </li>
            </swiper-slide> 
        </swiper>
    </ul>
    <div class="refers">
        <img class="like" src="https://imgs.qunarzz.com/piao/fusion/1711/89/ebc329f16c55bb02.png" alt="图片加载中...">
        <span class="prefer">猜你喜欢</span>
    </div>
    <ul>
        <li class="item" v-for="item in list" :key="item.id">
            <img class="item-img" :src="item.imgUrl">
            <div class="item-info">
                <p class="item-title">{{item.title}}</p>
                <p class="item-desc">{{item.desc}}</p>
                <button class="item-button">查看详情</button>
            </div>
        </li>
    </ul>
</div>
</template>

<script>
 export default {
   name: 'HomeRecommend',
   props: {
     list: Array,
   },
   data () {
     return {
      List:[
          {
              id: '0001',
              imgUrl: 'https://imgs.qunarzz.com/sight/p0/1411/1a/5582f9f24bc50b475a8cbda4c5ac8d24.water.jpg_150x150_7e9090b5.jpg',
              desc: '秦始皇陵博物院（兵马俑）',
              price: '266.3',
          },
          {
              id: '0002',
              imgUrl: 'https://imgs.qunarzz.com/sight/p0/1505/18/18ffcca94b1b7ca2.water.jpg_150x150_465a2539.jpg',
              desc: '长恨歌',
              price: '238',
          },
          {
              id: '0003',
              imgUrl: 'https://imgs.qunarzz.com/sight/p0/1411/b8/f5fd5955bdecc923ce6d40ce453160eb.water.jpg_150x150_5a0d2c02.jpg',
              desc: '陕西历史博物馆',
              price: '30',
          },
          {
              id: '0004',
              imgUrl: 'https://imgs.qunarzz.com/sight/p0/1602/de/de8400021b664c5390.img.jpg_150x150_760c98c0.jpg',
              desc: '华清宫（华清池·骊山）',
              price: '135',
          },
          {
              id: '0005',
              imgUrl: 'https://imgs.qunarzz.com/sight/p0/1508/db/dbd0bef45fbc36b3.img.jpg_150x150_048c0bd8.jpg',
              desc: '大唐芙蓉园',
              price: '89',

          },
          {
              id: '0006',
              imgUrl: 'https://imgs.qunarzz.com/sight/p0/1804/3d/3dda5c0b0085b8aa3.water.jpg_150x150_6cc5f21e.jpg',
              desc: '华夏文旅 《驼铃传奇》秀',
              price: '218',
          },
          {
              id: '0007',
              imgUrl: 'https://imgs.qunarzz.com/sight/p0/201403/21/83a2599d05c5ce25b76b0675eff7fd84.jpg_150x150_99098661.jpg',
              desc: '大慈恩寺（大雁塔）',
              price: '49',
          },
          {
              id: '0008',
              imgUrl: 'https://imgs.qunarzz.com/sight/p0/1412/84/f696c67a8052bb60e6fc51b0f9ba7388.water.jpg_150x150_91d09445.jpg',
              desc: '大明宫国家遗址公园',
              price: '60',
          },
          {
              id: '0009',
              imgUrl: 'https://imgs.qunarzz.com/sight/p0/1707/46/4628e1048dc22419a3.water.jpg_150x150_01c89357.jpg',
              desc: '永兴坊',
              price: '10',
          },
      ],
     }
   },
   computed: {
       pages() {
           const pages=[];
           this.List.forEach((item,index)=>{
               const page = Math.floor(index / 4);
               if(!pages[page]) {
                   pages[page] = []
               }
               pages[page].push(item)
           });
           return pages
       }
   },
   components: {
   }
 }
</script>

<style lang="stylus" scoped>
@import '~styles/mixins.styl'
.recommend-title
  margin-top: .2rem 
  background: #fff
  position: relative 
  padding: .24rem 0 .26rem
  .img 
    display: inline-block 
    overflow:hidden 
    width: .3rem 
    height: .3rem 
    margin-left: .2rem 
    vertical-align: top
  .hot 
    display: inline-block 
    margin-left: .08rem 
    height: .44rem 
    color: #212121
    font-size: .32rem 
    line-height: .44rem 
  .all 
    position: absolute 
    top: .36rem
    right: .32rem 
    color: #616161 
    font-size: .24rem 
    line-height: .28rem
.hot-list
  padding: 0 .24rem 
  white-space: nowrap
  .hot-item
    position: relative 
    display: inline-block 
    padding: .06rem 0 .2rem 
    width: 2rem
    .mp-fulllink
      display: block 
      width: 100% 
      height: 100%
      .mp-hotsale-imgcon
        overflow: hidden 
        width: 2rem 
        height: 0
        padding-bottom: 100%
        img 
          margin: 0 .1rem
          width: 100%
      .mp-hotsale-sight
        margin-top:.12rem 
        color: #212121 
        font-size: .24rem 
        line-height: .32rem 
        text-align: center
        ellipsis()
      .mp-hotsale-price
        color: #616161 
        font-size: .24rem 
        line-height: .36rem 
        text-align: center 
.refers 
  position: relative 
  padding: .24rem 0 .26rem
  .like 
    display: inline-block 
    overflow: hidden 
    width: .3rem 
    height: .3rem 
    margin-left: .2rem 
    vertical-align: top
  .prefer 
    display: inline-block 
    margin-left: .08rem 
    height: .44rem 
    color: #212121 
    font-size: .32rem 
    line-height: .44rem        
.item
  overflow: hidden
  display: flex
  height: 1.9rem
  .item-img
    width: 1.7rem
    height: 1.7rem
    padding: .1rem
  .item-info
    flex: 1
    padding: .1rem
    min-width: 0
    .item-title
      line-height: .54rem
      font-size: .32rem
      ellipsis()
    .item-desc
      line-height: .4rem
      color: #616161
      ellipsis()
    .item-button
      line-height: .44rem
      margin-top: .16rem
      background: #ff9300
      padding: 0 .2rem
      border-radius: .06rem
      color: #fff      
  
      
</style>