<template>
  <div id="app">
    <h4 class="top">计划</h4>
    <swiper :options="swiperOption" ref="mySwiper">
        <swiper-slide >
            <ul>
              <li class="dot">花费</li>
            </ul>
            <div  v-for="item in items">
              <p class="campaign">{{item.campaign_name}}</p>
              <ul>
                <li class="dots">{{item.cost}}</li>
              </ul>
            </div>
        </swiper-slide>
        <swiper-slide >
            <ul>
              <li class="dot">点击量</li>
            </ul>
             <div  v-for="item in items">
               <p class="campaign">&nbsp</p>
               <ul>
                  <li class="dots">{{item.clicks}}</li>
               </ul>
              </div>
        </swiper-slide>
        <swiper-slide>
            <ul>
              <li class="dot">展现量</li>
            </ul>
            <div  v-for="item in items">
               <p class="campaign">&nbsp</p>
               <ul>
                  <li class="dots">{{item.impressions}}</li>
               </ul>
              </div>
        </swiper-slide>
        <swiper-slide >
            <ul>
              <li class="dot">点击率</li>
            </ul>
            <div  v-for="item in items">
               <p class="campaign">&nbsp</p>
               <ul>
                  <li class="dots">{{item.ctr}}</li>
               </ul>
              </div>
        </swiper-slide>
        <swiper-slide >
            <ul>
              <li class="dot">CPM</li>
            </ul>
            <div  v-for="item in items">
               <p class="campaign">&nbsp</p>
               <ul>
                  <li class="dots">{{item.cpm}}</li>
               </ul>
              </div>
        </swiper-slide>
        <swiper-slide >
              <ul>
                 <li class="dot">CPC</li>
              </ul>
              <div  v-for="item in items">
              <p class="campaign">&nbsp</p>
               <ul>
                  <li class="dots">{{item.cpc}}</li>
               </ul>
              </div>
          </swiper-slide>
          <swiper-slide >
               <ul>
                  <li class="dot">订单数</li>
              </ul>
              <div  v-for="item in items">
              <p class="campaign">&nbsp</p>
               <ul>
                  <li class="dots">{{item.clicks}}</li>
               </ul>
              </div>
          </swiper-slide>
          <swiper-slide >
                <ul>
                  <li class="dot">订单金额</li>
                </ul>
                <div  v-for="item in items">
                   <p class="campaign">&nbsp</p>
               <ul>
                  <li class="dots">{{item.clicks}}</li>
               </ul>
              </div>
          </swiper-slide>
          <swiper-slide >
                <ul>
                  <li class="dot">投入产出比</li>
                </ul>
                <div  v-for="item in items">
                   <p class="campaign">&nbsp</p>
               <ul>
                  <li class="dots">{{item.clicks}}</li>
               </ul>
              </div>
          </swiper-slide>
  </swiper>
<div style="width:100%;clear:left"></div>
    <!-- <div>{{msg}}</div> -->
  </div>
</template>

<script>
import axios from 'axios'
import qs from 'qs'
import { Indicator } from 'mint-ui'
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'
export default {
  name:'recharge',
  components: {
    swiper,
    swiperSlide
  },
  data:function (){
      return{
         swiperOption: {
            slidesPerView: 3,
        },
        items:[]

      }
  },
   created(){
    var items=[{ad_type:3,campaign_id:111885590,campaign_name:"15日推广",campaign_status:2,campaign_visitor_cnt:48,clicks:57,cost:61.75,cpc:1.08,cpm:0.2,ctr:0.02,depth_passenger_cnt:2,
   impressions:311991,is_order_or_click:"点击",is_today_or_15days:"当天",mobile_type:"全部",order_status_category:"全部订单",put_type:"商品",visit_page_cnt:50,visit_time_range:9.9},
   {ad_type:3,campaign_id:111885590,campaign_name:"15日推广",campaign_status:2,campaign_visitor_cnt:48,clicks:57,cost:61.75,cpc:1.08,cpm:0.2,ctr:0.02,depth_passenger_cnt:2,
   impressions:311991,is_order_or_click:"点击",is_today_or_15days:"当天",mobile_type:"全部",order_status_category:"全部订单",put_type:"商品",visit_page_cnt:50,visit_time_range:9.9},
   {ad_type:3,campaign_id:111885590,campaign_name:"16日推广",campaign_status:2,campaign_visitor_cnt:48,clicks:57,cost:61.75,cpc:1.08,cpm:0.2,ctr:0.02,depth_passenger_cnt:2,
   impressions:311991,is_order_or_click:"点击",is_today_or_15days:"当天",mobile_type:"全部",order_status_category:"全部订单",put_type:"商品",visit_page_cnt:50,visit_time_range:9.9},
   {ad_type:3,campaign_id:111885590,campaign_name:"17日推广",campaign_status:2,campaign_visitor_cnt:48,clicks:57,cost:61.75,cpc:1.08,cpm:0.2,ctr:0.02,depth_passenger_cnt:2,
   impressions:311991,is_order_or_click:"点击",is_today_or_15days:"当天",mobile_type:"全部",order_status_category:"全部订单",put_type:"商品",visit_page_cnt:50,visit_time_range:9.9},
   {ad_type:3,campaign_id:111885590,campaign_name:"18日推广",campaign_status:2,campaign_visitor_cnt:48,clicks:57,cost:61.75,cpc:1.08,cpm:0.2,ctr:0.02,depth_passenger_cnt:2,
   impressions:311991,is_order_or_click:"点击",is_today_or_15days:"当天",mobile_type:"全部",order_status_category:"全部订单",put_type:"商品",visit_page_cnt:50,visit_time_range:9.9},
   {ad_type:3,campaign_id:111885590,campaign_name:"19日推广",campaign_status:2,campaign_visitor_cnt:48,clicks:57,cost:61.75,cpc:1.08,cpm:0.2,ctr:0.02,depth_passenger_cnt:2,
   impressions:311991,is_order_or_click:"点击",is_today_or_15days:"当天",mobile_type:"全部",order_status_category:"全部订单",put_type:"商品",visit_page_cnt:50,visit_time_range:9.9}
   ]
        Indicator.open({
            text: '加载中...',
            spinnerType: 'fading-circle'
        });
        var self = this;
        axios.get('/api/campaign/rpt?isTodayOr15Days=0&isOrderOrClick=0&platform=all&title=&campaignId=111885590').then(function (response) {

        }).catch(function (error) {
          self.items=items;
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
    ul{
      display:block;
      width:100%;
      display:flex;
    }
    ul .dot{
      line-height:100px;
      flex-grow:1;
      text-align: center;
      border-bottom:#f90 4px solid;
      position: relative;
      font-size:28px;
    }
    ul .dot:nth-child(1):after, ul .dot:nth-child(2):after, ul .dot:nth-child(3):after, ul .dot:nth-child(4):after, ul .dot:nth-child(5):after,
    ul .dot:nth-child(6):after, ul .dot:nth-child(7):after, ul .dot:nth-child(8):after, ul .dot:nth-child(9):after{
      content:"";
      width:4px;
      height:30px;
      background:#f90;
      position: absolute;
      right:0;
      bottom:0;
    }
    ul .dots{
      line-height:100px;
      flex-grow:1;
      text-align: center;
      border-bottom:#dedede 4px solid;
      position: relative;
      font-size:28px;
    }
    ul .dots:nth-child(1):after, ul .dots:nth-child(2):after, ul .dots:nth-child(3):after, ul .dots:nth-child(4):after, ul .dots:nth-child(5):after,
    ul .dots:nth-child(6):after, ul .dots:nth-child(7):after, ul .dots:nth-child(8):after, ul .dots:nth-child(9):after{
      content:"";
      width:4px;
      height:30px;
      background:#dedede;
      position: absolute;
      right:0;
      bottom:0;
    }
    .campaign{
      margin-top:50px;
      font-size:30px;
    }
</style>
