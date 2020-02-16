<template>
  <div class="recommend-info">
    <div class="info-header">热门推荐</div>
    <goods-list :goods="recommendInfo"></goods-list>
  </div>
</template>

<script>
import GoodsList from '@/components/content/goods/GoodsList'

export default {
  name: 'DetailRecommendInfo',
  components: {
    GoodsList
  },
  props: {
    recommendInfo: {
      type: Array,
      default () {
        return []
      }
    }
  }
}
</script>

<style scoped>

</style>
