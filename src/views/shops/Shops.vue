<style lang="less" scoped>
</style>
<template>
  <div class="Store">
    这是店铺模板页面。还没有做修饰。
    <hr />页面需要请求接口。返回店铺数据
    <h1>{{addr}}</h1>

    <h1>{{getDistributionTime}}</h1>
  </div>
</template>

<script>
export default {
  name: "Shops",
  data() {
    return {
      shopCeatgory: "自营",
      aa: true, //本地还是异地    true  -->本地   false  -->  异地
    };
  },
  components: {
    //组件
  },
  computed: {
    //计算
    addr() {
      //计算属性可以当成函数使用。 所以在计算属性中是可以做一些其他操作的。最后使用return返回值给函数名字即可

      let address = this.$store.state.ShoppingAddress.takeover_addr;
      address = address.split(",");
      address.pop();
      let temp = [];
      for (let i of address) {
        if (temp.indexOf(i) == -1) {
          temp.push(i);
        }
      }
      if (temp.length == 3) temp.pop();
      return temp.join(" ");
    },
    
  },
  created() {
    //创建
    this.setDate();
    this.setWeek();
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

    //从新获取日期
    setDate(nowTime= new Date(),day = 3){
      let temp = new Date(nowTime.getTime()+day*24*60*60*1000);
      temp = `${temp.getMonth()+1}月${temp.getDate()}日`;
      console.log(temp);
      return temp;
    },
    //从新获取星期几
    setWeek(nowTime= new Date(),day = 15){
      console.log(nowTime.getDay(),day);
      let nowWeek = nowTime.getDay();
      let temp=""
      if((nowWeek+day) > 7){
        temp = `下周${num(nowWeek+day-7)}`
      }else{
        temp = `本周${num(nowWeek+day)}`
      }
      function num (val){
        let a = ""
        switch(val%7){
          case 1: a='一'; break;
          case 2: a='二'; break;
          case 3: a='三'; break;
          case 4: a='四'; break;
          case 5: a='五'; break;
          case 6: a='六'; break;
          case 7: a='日'; break;
        }
        return a;
      }
      return temp;
    }
  },
  watch: {
    //监听
  },
};
</script>
