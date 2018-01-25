<template>
  <div>
      <h4 class="top">充值</h4>
      <nav>
        <!--  <div class="number">
            <span>{{msg}}</span>
            <p>账户余额（元）</p>
         </div> -->
         <input class="money" type="number" v-model.lazy="monkeynum" placeholder="请输入充值金额" >
      </nav>
      <div>
        <ul>
          <li v-for="(item,index) in objects" @click="getrecharge(item,index)" contextmenu="" :class="{active:index==nowIndex}">
              <p>{{item.data}}</p>
          </li>
          <div style="width:100%;clear:left"></div>
        </ul>
      </div>
        <!-- <input class="button" type="button" value="确认充值"> -->
        <a :href="href" class="button"  >确认充值</a>
  </div>
</template>

<script>
import { Toast } from 'mint-ui'
import axios from 'axios'
import qs from 'qs'
export default {
  name:'recharge',
  data:function (){
      return{
         msg:'0.00',
         monkeynum:'',
         nowIndex:null,
         arred:[],
         objects:[
            {data:'200'},
            {data:'500'},
            {data:'1000'},
            {data:'2000'},
            {data:'5000'},
            {data:'10000'}
          ]
      }
  },
  methods:{
    getrecharge(item,index){
        this.monkeynum=item.data;
        this.nowIndex=index;
    },

  },
  computed:{
    href(){
      if(this.monkeynum&&this.monkeynum<200){
       Toast('穷逼啊');
         return  false

      }
      if (this.monkeynum==''){
        return false
      }
      if(this.monkeynum>=200){
              return '/api/recharge?money='+this.monkeynum;
      }

    }
  },
   created(){
       /*  var self = this; */
        axios.get('/recharge?money=5')
            .then(function (response) {
                console.log(response.data);
               /*  self.msg=response.data.reduce(function(pre,next){return pre+next.cost},0);
                self.objects[0].data=response.data.reduce(function(pre,next){return pre+next.cost},0);
                self.objects[1].data=response.data.reduce(function(pre,next){return pre+next.clicks},0);
                self.objects[2].data=response.data.reduce(function(pre,next){return pre+next.impressions},0);
                self.objects[3].data=response.data.reduce(function(pre,next){return pre+next.ctr},0);
                self.objects[4].data=response.data.reduce(function(pre,next){return pre+next.cpm},0);
                self.objects[5].data=response.data.reduce(function(pre,next){return pre+next.cpc},0); */
        })
            .catch(function (error) {
                console.log(error);
        });
    },
  watch:{
      monkeynum(value){
        this.nowIndex=['200','500','1000','2000','5000','10000'].indexOf(value);
      }
  }
}
</script>
<style scoped>
  .top{
        width:100%;
        height:70px;
        line-height: 70px;
    }
    .number{
      width:100%;
      height: 150px;
      border-top:1px solid #dedede;
      border-bottom:1px solid #dedede;
    }
    .number>span{
      display:inline-block;
      color:orange;
      font-size:0.7rem;
      padding-top:10px;
    }
    .money{
      width:100%;
      height:90px;
      padding-left:16px;
      font-size:0.5rem;
      border:1px solid #dedede;
      margin-bottom:30px;
    }
    div ul{
        width:100%;
        border-top:1px solid #dedede;
        border-left:1px solid #dedede;
    }
    div ul li{
        float:left;
        width:33%;
        height:120px;
        border-bottom:1px solid #dedede;
        border-right:1px solid #dedede;
    }
    div ul li:nth-child(1),div ul li:nth-child(4){
      border-left:0;
    }
    div ul li:nth-child(3n){
        width:34%
    }
    div ul li p{
      font-weight: 300;
      font-size:0.6rem;
      line-height: 120px;
      padding:0;
    }
    .button{
      display:inline-block;
      margin-top:50px;
      width:96%;
      height:70px;
      line-height: 70px;
      background-color: orange;
      color:#fff;
      border:none;
      border-radius: 5px;
      font-size:0.4rem;
    }
    .active{
      border:1px solid orange;
      background-color:orange;
      opacity:.6;
    }
</style>
