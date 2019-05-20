<template>
  <div id="login">
    <table></table>
    <div class="head">
      <img src="../../public/loginImg/head.png" alt="">
    </div>
    <div class="body">
      <div class="ipts">
        <form action="http://127.0.0.1:3000/login">
          <div class="iptbox"><input v-model="phone" placeholder="手机号码" name="uphone" type="number"></div>
          <div class="iptbox"><input v-model="pwd" placeholder="密码" name="upwd" type="password">
         <button class="eye-btn">
            <img src="../../public/loginImg/eye.png" alt="">
         </button>
          </div>
          <div class="iptbox">
            <button type="submit" class="submit-btn" @click="btnLogin">登陆</button>
          </div>
        </form>
      </div> 
    </div>
    <div class="register">
      <ul>
        <li><router-link to="">
          忘记密码？
        </router-link></li>
        <li><router-link  to="">
         新用户注册
        </router-link></li>
      </ul>
    </div>
    <div class="bottom"></div>
  </div>
</template> 
<script> 
//在export 之前引入需要组件
import{Toast}from "mint-ui"
export default {
    data(){
       return{
          phone:"",
          pwd:""
       } 
    },
    methods:{
      btnLogin(e){
        e.preventDefault();
        console.log(1)
        console.log(this.phone)
       
       //创建正则表达是
       //电话号码11为
       var phoneUreg=/^1[3-8]\d{9}$/;
       if(!phoneUreg.test(this.phone)){
       Toast("手机号码不正确");
       return;
       }
       var pwdUrg=/^\d{6}$/;
       if(!pwdUrg.test(this.pwd)){
         Toast("密码不正确")
         return;
       }
       //发送ajax请求
       var url="http://127.0.0.1:3000/login"
      //  this.axios.post(url,{
      //   uphone:this.phone,
      //   upwd:this.pwd},
      //  ).then((res)=>{
      //    console.log(res)
      //  })
      this.axios({
        method:'post',
        url:url,
        data:{
          uphone:this.phone,
          upwd:this.pwd
        }
      });
      }
    }
    
}
</script>  
<style scope> 

 #login{
    min-height: 100%;
    background: url(../../public/loginImg/background.png) no-repeat center;
    background-size: cover;
}

 #login .head{
   margin:100px auto;
   width:40%;
  
 }
 #login .head>img{
   width:100%;
 }

 /* 表单元素样式 */
 #login .body .ipts{
   padding:0 60px;
 }

 #login .body .ipts .iptbox input{
   border-radius:20px;
   background:rgba(255,255,255,0.5)
 }
 #login .body .ipts form div:nth-child(2) input{
   width:80%;
   border-radius: 20px 0 0 20px;
   border-right:0;
 }
 #login .body .ipts form div:nth-child(2) button{
   width:20%;
   border-radius: 0 20px 20px 0;
   border:0;
   background:rgba(255,255,255,0.5);
   height:38.5px;
   margin-top:1px;
   
   
 }
 #login .body .ipts form div:nth-child(2) button img{
   width:100%;
   height:100%;

 }
 #login .body .ipts form div:nth-child(3) button {
   width:100%;
   border-radius: 20px;
   background:rgba(255,255,255,0.8);
   color:red;
   font-size:18px;
 }
 #login .register{
   padding:0 60px;
 }

 #login .register ul{
   display:flex;
   list-style: none;
   padding:0;
   justify-content: space-between;
   
 }
 #login .register ul a{
   color:#fff;
   font-size:13px;
 }

 #login .bottom{
   width:100%;
  height:210px;
  
 }
</style> 
