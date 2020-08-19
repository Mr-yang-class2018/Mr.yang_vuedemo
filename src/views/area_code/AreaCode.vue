<style lang="less" scoped>
#AreaCode{
    .scroll{
        position: absolute;
        top:49px;
        left:0;
        right:0;
        bottom:0;
        overflow: hidden;
        li{
            border-bottom:1px solid black;
            margin-bottom:3px;
            line-height:36px;
            display: flex;
            justify-content:space-between;
            padding:0 20px;
        }
    }
}
</style>
<template>
  <div id="AreaCode">
    <nav-bar>
      <div slot="left">
        <i class="el-icon-arrow-left" @click="$router.push('/register/0')"></i>
      </div>
      <div slot="center">选择国家或者地区</div>
      
    </nav-bar>
    <scroll class='scroll'>
        <ul>
            <li v-for='(item) in phone_area_code' :key="item.id" @click='checkCode(item.area_code)'>
                <span>{{item.country}}</span>
                <span>+{{item.area_code}}</span>
            </li>
        </ul>
    </scroll>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar";
import Scroll from 'components/contents/scroll/Scroll'
import { get_mobile_prefix } from "network/user";
export default {
  name: "AreaCode",
  data() {
    return {
        phone_area_code:null,
    };
  },
  components: {
    //组件
    NavBar,
    Scroll
  },
  computed: {
    //计算
  },
  created() {
    //创建
    get_mobile_prefix().then((res) => {
      this.phone_area_code = res.data;
    });
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
  methods: {
    //事件
    checkCode(val){
        this.$store.state.area_code = val;
        this.$router.push('/register/'+val)
    }
  },
  watch: {
    //监听
  },
};
</script>
