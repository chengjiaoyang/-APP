<template>
  <div class="page-tabbar">
    <div class="page-wrap">
        <router-view></router-view>
    </div>
    <mt-tabbar v-model="selected" fixed>
      <mt-tab-item id="home">
        <router-link to='/first'>
          <i class="iconfont icon-home"></i>
          <p>首页</p>
        </router-link>
      </mt-tab-item>
      <mt-tab-item id="manage">
        <router-link to='/manage'>
          <i class="iconfont icon-guanli"></i>
          <p>管理</p>
        </router-link>
      </mt-tab-item>
      <mt-tab-item id="recharge">
        <router-link to="/recharge">
          <i class="iconfont icon-3"></i>
          <p>充值</p>
        </router-link>
      </mt-tab-item>
    </mt-tabbar>
  </div>
</template>


<script>
export default {
  name: 'page-tabbar',
  data() {
    return {
      selected:'home',
      content:'home'
    }
  },
  created(){
    this.selected=sessionStorage.getItem('selected')||this.selected;
    this.selected=sessionStorage.getItem('content')||this.content
  },
  watch:{

    '$route.path'(value){

      value=value.slice(1)
      console.log(value);
        switch(value){
            case 'first':
          console.log('213-----------------------------------------------')
            this.content = 'home';
              this.selected = 'home';
            sessionStorage.clear()
            sessionStorage.setItem("selected","home")
            sessionStorage.setItem("content","home")
            break;
          case 'manage':
            this.content = 'manage';
              this.selected = 'manage';
            sessionStorage.clear()
            sessionStorage.setItem('selected',"manage")
            sessionStorage.setItem("content","manage")
            break;
          case 'recharge':
            this.content = 'recharge';
            this.selected = 'recharge';
            sessionStorage.clear()
          sessionStorage.setItem('selected',"recharge")
          sessionStorage.setItem("content","recharge")
            break;
        }
      }
  }

};
</script>

<style>
  .iconfont{
    display: block;
    font-size:0.6rem;
  }
  .page-tabbar {
    overflow: hidden;
    height: 100vh;
  }

  .page-wrap {
    overflow: auto;
    height: 100%;
    padding-bottom: 100px;
  }
  p{
    padding-top:10px;
  }
</style>
