<template>
  <div class="classify-wrapper">
    <div class="search-btn">
      <van-icon name="search" />
      <div>苹果特价1元1斤</div>
    </div>
    <one-tab></one-tab>
    <template v-if="true">
      <side-bar />
      <goods-list />
    </template>
<!--    <van-loading size="2rem" vertical />-->
  </div>
</template>

<script>
import oneTab from '../components/OneTab.vue';
import sideBar from '../components/SideBar.vue';
import goodsList from '../components/GoodsList.vue';

export default {
  components: {
    oneTab,
    sideBar,
    goodsList,
  },
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
  .classify-wrapper {
    width: 375px;
    .search-btn {
      width: 355px;
      height: 33px;
      line-height: 33px;
      background-color: #eee;
      margin: 11px auto 0;
      border-radius: 10px;
      font-size: 14px;
      text-align: center;
      color: #a1a1a1;
      >* {
        display: inline-block;
        vertical-align: middle;
      }
    }
  }
</style>
