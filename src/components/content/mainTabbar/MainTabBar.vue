<template>
  <tab-bar>
    <tab-bar-item path="/home">
      <img slot="item-icon" src="~@/assets/img/tabbar/home.svg" alt="">
      <img slot="item-icon-active" src="~@/assets/img/tabbar/home-active.svg" alt="">
      <div slot="item-text">首页</div>
    </tab-bar-item>
    <tab-bar-item path="/category">
      <img slot="item-icon" src="~@/assets/img/tabbar/category.svg" alt="">
      <img slot="item-icon-active" src="~@/assets/img/tabbar/category-active.svg" alt="">
      <div slot="item-text">分类</div>
    </tab-bar-item>
    <tab-bar-item path="/cart">
      <img slot="item-icon" src="~@/assets/img/tabbar/shopcart.svg" alt="">
      <img slot="item-icon-active" src="~@/assets/img/tabbar/shopcart-active.svg" alt="">
      <div slot="item-text">购物车</div>
    </tab-bar-item>
    <tab-bar-item path="/account">
      <img slot="item-icon" src="~@/assets/img/tabbar/account.svg" alt="">
      <img slot="item-icon-active" src="~@/assets/img/tabbar/account-active.svg" alt="">
      <div slot="item-text">我的</div>
    </tab-bar-item>
  </tab-bar>
</template>

<script>
import TabBarItem from '@/components/common/tabbar/TabBarItem'
import TabBar from '@/components/common/tabbar/TabBar'

export default {
  name: 'MainTabBar',
  components: {
    TabBarItem,
    TabBar
  },
  computed: {
    // isDetailView () {
    //   console.log(this.$route)
    //   return this.$rourt.indexOf('detail') !== -1
    // }
  }
}
</script>

<style scoped>

</style>
