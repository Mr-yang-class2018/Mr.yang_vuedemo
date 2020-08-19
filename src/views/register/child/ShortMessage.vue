<style lang="less" scoped>
</style>
<template>
  <div class='ShortMessage'>
      <h1>发送短信</h1>
  </div>
</template>

<script>
export default {
  name: 'ShortMessage',
  data(){
    return {}
  },
  components: {//组件
  },
  computed: {//计算
  },
  created(){//创建
  },
  activated(){//激活
  },
  deactivated(){//未激活
  },
  mounted(){//渲染
  },
  methods: {//事件
  },
  watch: {//监听
  },
}
</script>
<script>

import NavBar from "components/common/navbar/NavBar";
import {regPhone,get_mobile_prefix} from 'network/user'
export default {
  name: '',
  data(){
    return {
        region:"",
        phone:"",
        phone_area_code:null,//国际区号
        regTel:true,
        area_code:"86"
    }
  },
  components: {//组件
    NavBar
  },
  watch: {//监听
    phone(val){
        let pattern =/^(13|14|15|17|18)[0-9]{9}$/;
        this.regTel = !pattern.test(val)
    },
    area_code(){
      console.log
    }
  },
  methods: {//事件
    changeRegion(){},
    next(){
        var data={telphone:this.phone}
        regPhone(data).then(res=>{
            console.log(res);
            // res.code == 500 代表用于已经注册 
            if(res.code == 500){
              //把用户注册的时间提取出来。转换成时间格式  2020-06-26T06:42:43.000Z
              let createTime = new Date(res.data.createtime)
              let newDate = new Date()
              //Difference  差值毫秒数
              //   new Date().getTime()  获取当前时间到1970年的毫秒值
              let Difference = newDate.getTime() - createTime.getTime();
              if( Difference > 30*24*60*60*1000){ 
                //注册时间大于3天  跳转页面  并传递用户数据过去
                this.$router.push('/registered/'+JSON.stringify(res.data))
                return
              }
              alert("该手机号已被其他账号绑定,30天内不可改绑")
              return
            }
            let  data ={};
            data.areaCode = this.areaCode;
            data.phone = this.phone;
            //如果不是500 ,手机号是未被注册的，跳转短信页面  并传递电话信息过去
            this.$router.push('/shortmeg/'+JSON.stringify(data))
        })
    }
  },
  created(){//创建
    get_mobile_prefix().then(res=>{
      this.phone_area_code = res.data
      console.log(this.phone_area_code);
    })
  },
  activated(){//激活
  },
  deactivated(){//未激活
  },
  mounted(){//渲染
  },
  filters:{
      regPhone(val){
          let pattern = /^0?(13|14|15|17|18)[0-9]{9}$/;
          return pattern.test(val)
      }
  }
}
</script>
