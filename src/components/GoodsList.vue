<template>
  <div class="list-wrapper">
    <div class="list-header van-hairline--top-bottom">
      <div
        :class="{active: type == 'all'}"
        @click="changeType('all')"
      >综合
      </div>
      <div
        :class="{active: type == 'sale'}"
        @click="changeType('sale')"
      >销量
      </div>
      <div
        class="price"
        @click="changeType('price')"
        :class="{'price-up': type == 'price-up', 'price-down': type == 'price-down'}"
      >价格
      </div>
    </div>
    <div class="list-content">
      <van-pull-refresh v-model="isLoading" @refresh="onRefresh">
        <van-list
          v-model="loading"
          :finished="finished"
          finished-text="没有了"
          @load="onLoad"
          :mmediate-check="false"
        >
          <goods-card
            v-for="item in goodsList"
            :key="item.id"
            v-bind="item"
          ></goods-card>
        </van-list>
      </van-pull-refresh>
    </div>
  </div>
</template>

<script>
import goodsCard from './GoodsCard.vue';

export default {
  data() {
    return {
      type: 'all',
      isLoading: false,
      loading: false,
      finished: false,
      page: 1,
      goodsList: [1, 2, 4, 5],
    };
  },
  components: {
    goodsCard,
  },
  computed: {},
  methods: {
    // onRefresh() {
    //   // this.isloading = true;
    //   this.finished = false;
    //   this.loading = false;
    //   this.page = 1;
    //   // this.resetGoodsList();
    //   // this.getGoodsList({ page: 1, sortType: this.type });
    //   this.isLoading = false;
    // },
  },
};
</script>

<style lang="scss">
  .list-header {
    width: 296px;
    position: relative;
    top: 0;
    left: 79px;
    box-sizing: border-box;
    padding: 0 8px;
    display: flex;
    justify-content: flex-end;

    > div {
      width: 50px;
      height: 25px;
      line-height: 25px;
      text-align: center;
      color: #cecece;
      position: relative;
    }

    .active, .price-up, .price-down {
      color: #ff1a90;
      font-weight: bold;
    }

    .price::after {
      content: '';
      border: 4px solid transparent;
      border-top-color: #aaa;
      position: absolute;
      bottom: 4px;
      right: 0;
    }

    .price::before {
      content: '';
      border: 4px solid transparent;
      border-bottom-color: #aaa;
      position: absolute;
      top: 4px;
      right: 0;
    }

    .price-up::before {
      border-bottom-color: #ff1a90;
    }

    .price-down::after {
      border-top-color: #ff1a90;
    }
  }

  .list-content {
    width: 296px;
    position: fixed;
    top: 170px;
    right: 0;
    bottom: 50px;
    overflow: auto;
  }

  .van-pull-refresh {
    overflow: unset !important;
  }
</style>
