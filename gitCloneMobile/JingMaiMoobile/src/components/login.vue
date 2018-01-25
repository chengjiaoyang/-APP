<template>
  <div>
      <p>登录系统</p>
      <form action="/api/user/login" method="post">
          <input type="text" name="text" id="text" v-model="loginForm.uname" ></br>
          <input type="password" name="password" id="password" v-model="loginForm.passwd" ></br>
          <button @click="signin" type="button">登录</button>
      </form>
  </div>
</template>

<script>
import { Toast } from 'mint-ui'
import axios from 'axios'
import qs from 'qs'
export default {
  data() {
      return {
        loading: false,
        loginForm: {
          uname: '',
          passwd: ''
        },
        loginRule: {
          uname: [
            { required: true, message: '请输入用户名', trigger: 'blur' }
          ],
          passwd: [
            { required: true, message: '请输入密码', trigger: 'blur' },
            { type: 'string', min: 6, message: '密码长度不能少于6个字符', trigger: 'blur' }
          ]
        }
      }
    },
    methods: {
      signin(){
        if(!this.loginForm.uname)
          return  Toast('用户名不能为空')
        if(this.loginForm.uname!=='天喜日本生活专营店')
        return Toast('用户名错误')
          if(!this.loginForm.passwd)
            return  Toast('密码不能为空')
        if(this.loginForm.passwd&&this.loginForm.passwd.length<6){
          return Toast('密码长度不能少于6个字符')
        }
      if(this.loginForm.uname&&this.loginForm.passwd.length>=6)
           {
            this.$router.push({
            name:'first',
          });
      console.log(this.loginForm);
      axios.post('/api/user/login', 'uname=' +this.loginForm.uname +'&passwd='+this.loginForm.passwd, {headers: {'Content-Type': 'application/x-www-form-urlencoded'}}).then((response)=>{});
   /*    axios({
          headers: {
                          
                      },
        method:'post',
        url:'/api/user/login',
        data:{
          uname:this.loginForm.uname,
          passwd:this.loginForm.passwd
        }
      }) */
        /*   axios.post('/api/user/login', this.loginForm,  {
                      headers: {
                            'Content-Type': 'application/x-www-form-urlencoded'
                      }
                  })
                .then(function (response) {
                  console.log(response);
                })
                .catch(function (error) {
                  console.log(error);
            }); */

          /*   var ajax = new XMLHttpRequest();
            ajax.open('post','/api/user/login',true);
            ajax.setRequestHeader('content-type','application/x-www-form-urlencoded');
            ajax.send('uname='+this.loginForm.uname+'&passwd='+this.loginForm.passwd);
            ajax.onreadystatechange = function(){
                if(ajax.readyState==4 && ajax.status==200){
                    console.log(ajax.responseText);
                    console.log('成功');
                  }
            }  */
        }
        else
          Toast('用户名密码错误')
      }
    },
    computed: {

    }
}
</script>

<style scoped>
  p{
    margin-top:200px;
    padding-bottom:30px;
  }
  input{
    margin-bottom:30px;
    border:1px solid #dedede;
    border-radius: 5px;
  }
  button{
    width:230px;
    border-radius: 5px;
    border:1px solid #dedede;
    background: orange;
  }
</style>