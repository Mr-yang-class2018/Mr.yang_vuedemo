<style lang="less" scoped>
</style>
<template>
  <div class="Store">
    <div class='head'>
      <div>
        这是店铺模板页面。还没有做修饰。
        <img src="" alt="店铺logo" class='logo'>
        <div class='title'>店铺名</div>
        <button>收藏</button>
        <button title='更多'>...</button>
      </div>
      <div class='nav'>
        <button title='有个点击事件，点击可以跳转到搜索页面'> <span>搜索图标</span>   搜索</button>
        <ul>
          <router-link tag='li' to="/page1">首页1</router-link>
          <router-link tag='li' to="/page3">首页3</router-link>
          <router-link tag='li' to="/page4">首页4</router-link>
          <router-link tag='li' to="/page5">首页5</router-link>
          <router-link tag='li' to="/page7">首页7</router-link>
          <router-link tag='li' to="/page9">首页9</router-link>
        </ul>
      </div>
      <router-view>
        我不会写！
      </router-view>
    </div>

      


  </div>
</template>

<script>
export default {
  name: "Shops",
  data() {
    return {};
  },
  components: {
    //组件
  },
  computed: {},
  created() {
    let a = [
      {
        goods_id: "7",
        goods_name:
          "舌里%20蛋黄酥12枚装雪媚娘饼干蛋糕早餐代餐网红面包休闲零食小吃500g/箱",
        money_now: "19.9",
        money_old: "25",
        norm: "{}",
        num: 1,
        shop_id: 8,
        takeover_addr: "北京市,北京市,昌平区,",
        user_id: 14,
      },
      {
        goods_id: "21",
        goods_name:
          "南极人女鞋夏季气垫鞋休闲鞋女士飞织透气女时尚学生板鞋运动跑步鞋韩版百搭潮鞋网鞋镂空",
        money_now: "73",
        money_old: "80",
        norm: "{}",
        num: 1,
        shop_id: 4,
        takeover_addr: "北京市,北京市,昌平区,",
        user_id: 14,
      },
    ];
    console.log(a);
  },
  activated() {
    //激活
  },
  deactivated() {
    //未激活
  },
  mounted() {
    //渲染
  },
  methods: {},
  watch: {
    //监听
  },
};
</script>
