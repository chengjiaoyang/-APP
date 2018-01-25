<template>
    <div>
        <h4 class="top">直通车官方应用</h4>
        <header>
            <div class="number">
                <p>昨日花费（元）</p>
                <span>{{msg}}</span>
            </div>
           <!--  <div class="number">
                <p>账户余额</p>
                <span>{{msg}}</span>
            </div> -->
            <router-link :to="{path:'/recharge'}">
                <div class="car">直通车充值</div>
            </router-link>

        </header>
        <nav>
            <div class="timenumber">
                <p>昨日数据</p>
            </div>
            <ul>
                <li v-for="item in objects">
                    <p>{{item.title}}</p>
                    <span>{{item.data}}</span>
                </li>
                <div style="width:100%;clear:left"></div>
            </ul>
        </nav>
    </div>
</template>

<script>
import axios from 'axios'
import qs from 'qs'
import { Indicator } from 'mint-ui'
export default {
    name:'first',
    data (){
        return{
            msg:'0',
            objects:[
                {title:'花费（元）', data:null},
                {title:'点击量', data:null},
                {title:'展现量', data:null},
                {title:'点击率', data:null},
                {title:'CPM', data:null},
                {title:'CPC', data:null},
                {title:'订单数', data:null},
                {title:'订单金额', data:null},
                {title:'投入产出比', data:null}
            ],
            selected:'tab1'
        }
    },
    created(){
        Indicator.open({
            text: '加载中...',
            spinnerType: 'fading-circle'
        });
        var arrs = [{ad_type:3,campaign_id:111885590,campaign_name:"15日推广",campaign_status:2,campaign_visitor_cnt:48,clicks:57,cpc:1.08,cpm:0.2,ctr:0.02,depth_passenger_cnt:2,
    impressions:311991,is_order_or_click:"点击",is_today_or_15days:"当天",mobile_type:"全部",order_status_category:"全部订单",put_type:"商品",visit_page_cnt:50,visit_time_range:9.9},
    {ad_type:3,campaign_id:111885590,campaign_name:"15日推广",campaign_status:2,campaign_visitor_cnt:48,clicks:57,cost:61.75,cpc:1.08,cpm:0.2,ctr:0.02,depth_passenger_cnt:2,
    impressions:311991,is_order_or_click:"点击",is_today_or_15days:"当天",mobile_type:"全部",order_status_category:"全部订单",put_type:"商品",visit_page_cnt:50,visit_time_range:9.9},
    {ad_type:3,campaign_id:111885590,campaign_name:"15日推广",campaign_status:2,campaign_visitor_cnt:48,clicks:57,cost:61.75,cpc:1.08,cpm:0.2,ctr:0.02,depth_passenger_cnt:2,
    impressions:311991,is_order_or_click:"点击",is_today_or_15days:"当天",mobile_type:"全部",order_status_category:"全部订单",put_type:"商品",visit_page_cnt:50,visit_time_range:9.9},
    {ad_type:3,campaign_id:111885590,campaign_name:"15日推广",campaign_status:2,campaign_visitor_cnt:48,clicks:57,cost:61.75,cpc:1.08,cpm:0.2,ctr:0.02,depth_passenger_cnt:2,
    impressions:311991,is_order_or_click:"点击",is_today_or_15days:"当天",mobile_type:"全部",order_status_category:"全部订单",put_type:"商品",visit_page_cnt:50,visit_time_range:9.9},
    {ad_type:3,campaign_id:111885590,campaign_name:"15日推广",campaign_status:2,campaign_visitor_cnt:48,clicks:57,cost:61.75,cpc:1.08,cpm:0.2,ctr:0.02,depth_passenger_cnt:2,
    impressions:311991,is_order_or_click:"点击",is_today_or_15days:"当天",mobile_type:"全部",order_status_category:"全部订单",put_type:"商品",visit_page_cnt:50,visit_time_range:9.9},
    {ad_type:3,campaign_id:111885590,campaign_name:"15日推广",campaign_status:2,campaign_visitor_cnt:48,clicks:57,cost:61.75,cpc:1.08,cpm:0.2,ctr:0.02,depth_passenger_cnt:2,
    impressions:311991,is_order_or_click:"点击",is_today_or_15days:"当天",mobile_type:"全部",order_status_category:"全部订单",put_type:"商品",visit_page_cnt:50,visit_time_range:9.9}
    ]
        var self = this;
        axios.get('/api/campaign/rpt?isTodayOr15Days=0&isOrderOrClick=0&platform=all&title=&campaignId=111885590')
            .then(function (response) {
                console.log(response.data);

        })
            .catch(function (error) {
              self.msg=arrs.reduce(function(pre,next){return pre+next.cost},0);
              self.objects[0].data=arrs.reduce(function(pre,next){return pre+next.cost},0);
              self.objects[1].data=arrs.reduce(function(pre,next){return pre+next.clicks},0);
              self.objects[2].data=arrs.reduce(function(pre,next){return pre+next.impressions},0);
              self.objects[3].data=arrs.reduce(function(pre,next){return pre+next.ctr},0);
              self.objects[4].data=arrs.reduce(function(pre,next){return pre+next.cpm},0);
              self.objects[5].data=arrs.reduce(function(pre,next){return pre+next.cpc},0);
              self.objects[6].data=arrs.reduce(
                  (pre,next)=>{
                      if(next.total_order_sum){
                          return pre+next.total_order_sum
                      }else{
                          return pre + 0
                      }
                  },0);
              self.objects[7].data=arrs.reduce(
                  (pre,next)=>{
                      if(next.total_order_cnt){
                          return pre+next.total_order_cnt
                      }else{
                          return pre + 0
                      }
                  },0);
              self.objects[8].data=arrs.reduce(
                  (pre,next)=>{
                      if(next.total_order_roi){
                          return pre+next.total_order_roi
                      }else{
                          return pre + 0
                      }
                  },0);
                  Indicator.close();
        });

    }
}
</script>

<style scoped>
    .top{
        width:100%;
        height:70px;
        line-height: 70px;
    }
    header{
        width:100%;
        height: 150px;
        background-color: orange;
        color:#fff;
    }
    .number{
        float:left;
        padding-top:20px;
        padding-left:20px;
    }
    .number p{
        font-size:0.4rem;
    }
    .number>span{
        display:inline-block;
        padding-top:2px;
        font-size:0.6rem;
    }
    .car{
        float:right;
        margin:50px 20px 0 0;
        display:inline-block;
        width:170px;
        height:50px;
        line-height: 50px;
        border-radius:8px;
        border:1px solid #dedede;
        color:#fff;
    }
    .timenumber{
        margin:30px 0;
    }
    .timenumber p{
        font-size:0.4rem;
    }
    nav ul{
        width:100%;
        border-top:1px solid #dedede;
        border-left:1px solid #dedede;
    }
    nav ul li{
        float:left;
        width:33%;
        height:220px;
        border-bottom:1px solid #dedede;
        border-right:1px solid #dedede;
    }
    nav ul li:nth-child(3n){
        width:34%
    }
    nav ul li p{
        padding-top:58px;
        font-size:0.4rem;
    }
    nav ul li span{
        display: inline-block;
        padding-top:10px;
        color:orange;
        font-size:0.8rem;
    }
</style>
