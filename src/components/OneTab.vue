<template>
  <div class="one-tab-wrapper" ref="oneTab">
    <div class="tab-item"
         v-for="(item, i) in menuList"
         :key="item.title"
         :class="{active: index == i}"
         @touchend="scrollTo(i, $event)"
         @touchstart="move = false"
         @touchmove="move = true"
    >
      <div class="img-wrapper">
        <img :src="item.imgURL">
      </div>
      <div class="tab-title">{{ item.title }}</div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      move: false,
      index: 0,
      menuList: [
        {
          title: '时令水果',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/时令水果.jpg',
        },
        {
          title: '酒水冲调',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/酒水冲调.jpg',
        },
        {
          title: '安心乳品',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/安心乳品.jpg',
        },
        {
          title: '休闲零食',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/休闲零食.jpg',
        },
        {
          title: '肉蛋食材',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/肉蛋食材.jpg',
        },
        {
          title: '新鲜蔬菜',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/新鲜食材.jpg',
        },
        {
          title: '熟食餐饮',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/熟食餐饮.jpg',
        },
        {
          title: '海鲜水产',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/海鲜水产.jpg',
        },
        {
          title: '粮油调味',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/粮油调味.jpg',
        },
        {
          title: '某手美食',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/某手美食.jpg',
        },
        {
          title: '纸杯清洁',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/纸品清洁.jpg',
        },
        {
          title: '个人护理',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/个人护理.jpg',
        },
        {
          title: '美妆护肤',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/美妆护肤.jpg',
        },
        {
          title: '家居收纳',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/家居收纳.jpg',
        },
        {
          title: '家用电器',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/家用电器.jpg',
        },
        {
          title: '3C数码',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/3C数码.jpg',
        },
        {
          title: '母婴用品',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/母婴用品.jpg',
        },
        {
          title: '鲜花绿植',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/鲜花绿植.jpg',
        },
        {
          title: '宠物用品',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/宠物用品.jpg',
        },
        {
          title: '图书玩具',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/图书文具.jpg',
        },
        {
          title: '手表配饰',
          imgURL:
            'https://duyi-bucket.oss-cn-beijing.aliyuncs.com/img/手表配饰.jpg',
        },
      ],
    };
  },
  methods: {
    /**
     * i - 选中的index下标
     * e - 事件对象源
     * */
    scrollTo(i, e) {
      // 若果正在移动就什么都不做，如果是点击就执行下面的函数
      if (this.move) {
        return;
      }
      this.index = i; // 获取并赋值被选中的icon下标
      // 计算移动的距离
      const { oneTab } = this.$refs; // 获取当前元素（父级）
      const itemWidth = e.target.offsetWidth; // 当前选中icon的宽度
      const itemLeft = e.target.getBoundingClientRect().left; // 当前选中icon左边距
      const wrapperWidth = oneTab.offsetWidth; // 父级元素的宽度
      this.moveTo(oneTab.scrollLeft, itemWidth / 2 + itemLeft - wrapperWidth / 2); // 让选中的icon居中
    },
    moveTo(start, end) {
      let dis = 0;
      let speed = 5;
      if (end < 0) {
        speed *= -1;
      }
      const t = setInterval(() => {
        dis += speed;
        this.$refs.oneTab.scrollLeft = start + dis;
        if (Math.abs(dis) > Math.abs(end)) {
          this.$refs.oneTab.scrollLeft = start + end;
          clearInterval(t);
        }
      });
    },
  //   scrollTo(i, e) {
  //     if (this.move) {
  //       return;
  //     }
  //     this.index = i;
  //     // 移动到中间
  //     //  1. 父级元素的宽度 - 当前选中元素的宽度（左边距-宽度/2);
  //     const { oneTab } = this.$refs;
  //     const itemWidth = e.target.offsetWidth;
  //     const itemLeft = e.target.offsetLeft;
  //     const wrapperWidth = oneTab.offsetWidth;
  //     console.log(itemWidth, oneTab, wrapperWidth, itemLeft);
  //     oneTab.scrollLeft = itemWidth / 2 + itemLeft - wrapperWidth / 2;
  //   },
  },
};
</script>

<style lang='scss' scoped>
  .one-tab-wrapper {
    width: 375px;
    height: 104px;
    display: flex;
    overflow-y: hidden;
    .tab-item {
      width: 50px;
      height: 70px;
      padding: 10px 5px;
      .img-wrapper {
        width: 50px;
        height: 50px;
        display: flex;
        justify-content: center;
        align-content: center;
        border-width: 2px;
        border-style: solid;
        border-color: #fff;
        border-radius: 23px;
        img {
          width: 45px;
          height: 45px;
          border-radius: 50%;
          align-self: center;
        }
      }
      .tab-title {
        text-align: center;
        font-size: 11px;
        margin-top: 5px;
      }
    }
    .active {
      .img-wrapper {
        border-color: #d13193;
      }
      .tab-title {
        color: #fff;
        background-color: #d13193;
        font-weight: bold;
        border-radius: 30px;
      }
    }
  }
  .one-tab-wrapper::-webkit-scrollbar {
    width: 0px;
    background: none;
  }
</style>
