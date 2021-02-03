<template>
  <div class="sidebar-wrapper" ref="side">
    <div
      v-for="(item, i) in sideList"
      :key="item"
      :class="{active: index === i}"
      @touchend="scrollTo(i, $event)"
      @touchstart="move = false"
      @touchmove="move = true"
    >{{ i == 0 ? '全部' : item}}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      index: 0,
      sideList: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 21, 14, 15],
    };
  },
  computed: {

  },
  methods: {

  },
  mounted() {

  },
};
</script>

<style lang="scss" scoped>
  .sidebar-wrapper {
    position: fixed;
    left: 0px;
    width: 79px;
    top: 135px;
    bottom: 50px;
    overflow: auto;
    background: #f8f8f8;
    div {
      width: 79px;
      text-align: center;
      height: 40px;
      line-height: 40px;
      position: relative;
    }
    .active {
      font-weight: bold;
      color: #ff1a90;
    }
    .active::before {
      position: absolute;
      width: 6px;
      height: 18px;
      background-color: #ff1a90;
      top: 50%;
      transform: translateY(-50%);
      left: 0;
      content: "";
    }
  }
  .sidebar-wrapper::-webkit-scrollbar {
    width: 0px;
    background: none;
  }
</style>
