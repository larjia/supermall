<template>
  <div id="detail">
    <detail-nav-bar/>
    <scroll class="content"
      ref="scroll"
      :prob-type="3">
      <detail-swiper :top-images="topImages"></detail-swiper>
      <detail-base-info :goods="goods"></detail-base-info>
      <detail-shop-info :shop="shop"></detail-shop-info>
      <detail-goods-info :detail-info="detailInfo"></detail-goods-info>
      <detail-param-info :param-info="paramInfo"></detail-param-info>
      <detail-comment-info :comment-info="commentInfo"></detail-comment-info>
      <detail-recommend-info :recommend-info="recommendInfo"></detail-recommend-info>
    </scroll>
  </div>
</template>

<script>
import Scroll from '@/components/common/scroll/Scroll'

import DetailNavBar from './childComps/DetailNavBar'
import DetailSwiper from './childComps/DetailSwiper'
import DetailBaseInfo from './childComps/DetailBaseInfo'
import DetailShopInfo from './childComps/DetailShopInfo'
import DetailGoodsInfo from './childComps/DetailGoodsInfo'
import DetailParamInfo from './childComps/DetailParamInfo'
import DetailCommentInfo from './childComps/DetailCommentInfo'
import DetailRecommendInfo from './childComps/DetailRecommendInfo'

import { getDetail, Goods, Shop, GoodsParam, getRecommend } from '@/network/detail'

export default {
  name: 'Detail',
  components: {
    DetailNavBar,
    DetailSwiper,
    DetailBaseInfo,
    DetailShopInfo,
    DetailGoodsInfo,
    DetailParamInfo,
    DetailCommentInfo,
    DetailRecommendInfo,
    Scroll
  },
  data () {
    return {
      iid: null,
      topImages: [],
      goods: {},
      shop: {},
      detailInfo: {},
      paramInfo: {},
      commentInfo: {},
      recommendInfo: []
    }
  },
  created () {
    // 1. 保存传入的iid
    this.iid = this.$route.params.iid

    // 2. 根据iid请求详情数据
    getDetail(this.iid).then(res => {
      console.log(res)
      // 2.1 - 获取结果
      const data = res.result
      // 2.2 - 获取顶部的图片轮播数据
      this.topImages = res.result.itemInfo.topImages
      // 2.3 - 获取商品信息
      this.goods = new Goods(data.itemInfo, data.columns, data.shopInfo.services)
      // 2.4 - 创建店铺信息的对象
      this.shop = new Shop(data.shopInfo)
      // 2.5 - 获取商品信息
      this.detailInfo = data.detailInfo
      // 2.6 保存参数信息
      this.paramInfo = new GoodsParam(data.itemParams.info, data.itemParams.rule)
      // 2.7 - 保存评论信息
      if (data.rate.list) {
        this.commentInfo = data.rate.list[0]
      }
    })

    // 3. 请求推荐书籍
    getRecommend().then(res => {
      this.recommendInfo = res.data.list
    })
  }
}
</script>

<style scoped>
  #detail {
    height: 100vh;
    position: relative;
    /* z-index: 1; */
    background-color: #fff;
  }

  .content {
    position: absolute;
    top: 44px;
    bottom: 60px;
  }
</style>
