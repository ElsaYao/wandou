<template>
  <div id="main">
    <div class="log">
        <table></table>
        <div class="top">
            <img src="../../public/mainpageImg/w.png" alt="">
            <span><router-link to="/Login">点击登录 /  </router-link></span>
            <span><router-link to="/Login">注册</router-link></span>
        </div>
        <ul class="bottom">
            <li>
                <span>-</span>
                <p><router-link to="">抵现积分</router-link></p>
                
            </li>
            <li>
                <span>-</span>
                <p><router-link to="">优惠券</router-link></p>
            </li>
            <li>
                <span>-</span>
                <p><router-link to="">公主说</router-link></p>
            </li>
        </ul>
    </div>
    <div class="myOrder">
        <p>我的订单</p>
        <ul>
            <li>
                <img src="../../public/mainpageImg/nopay.png" alt="">
                <p>待付款</p>
            </li>
            <li>
                <img src="../../public/mainpageImg/noship.png" alt="">
                <p>待发货</p>
            </li>
            <li>
                <img src="../../public/mainpageImg/noreceive.png" alt="">
                <p>待收货</p>
            </li>
            <li>
                <img src="../../public/mainpageImg/nofeedback.png" alt="">
                <p>待评价</p>
            </li>
            <li>
                <img src="../../public/mainpageImg/allorders.png" alt="">
                <p>全部订单</p>
            </li>
        </ul>
    </div>
    <div class="myOrder">
            <p>我的订单</p>
            <ul>
                <li>
                    <img src="../../public/mainpageImg/nopay.png" alt="">
                    <p>待付款</p>
                </li>
                <li>
                    <img src="../../public/mainpageImg/noship.png" alt="">
                    <p>待发货</p>
                </li>
                <li>
                    <img src="../../public/mainpageImg/noreceive.png" alt="">
                    <p>待收货</p>
                </li>
                <li>
                    <img src="../../public/mainpageImg/nofeedback.png" alt="">
                    <p>待评价</p>
                </li>
                <li>
                    <img src="../../public/mainpageImg/allorders.png" alt="">
                    <p>全部订单</p>
                </li>
            </ul>
        </div>
        <div class="myOrder">
                <p>我的订单</p>
                <ul>
                    <li>
                        <img src="../../public/mainpageImg/nopay.png" alt="">
                        <p>待付款</p>
                    </li>
                    <li>
                        <img src="../../public/mainpageImg/noship.png" alt="">
                        <p>待发货</p>
                    </li>
                    <li>
                        <img src="../../public/mainpageImg/noreceive.png" alt="">
                        <p>待收货</p>
                    </li>
                    <li>
                        <img src="../../public/mainpageImg/nofeedback.png" alt="">
                        <p>待评价</p>
                    </li>
                    <li>
                        <img src="../../public/mainpageImg/allorders.png" alt="">
                        <p>全部订单</p>
                    </li>
                </ul>
           </div>
    <my-footer></my-footer>       
  </div>  
  
</template>  
<script>
import myFooter from "@/components/footer.vue"   
export default {
    data(){
       return{
          
       } 
    },
    components:{
        myFooter
    }
    
}
</script> 
<style scope>
    /* 登陆注册框样式 */
  /*所有字体都是白色  */
#main{
    padding:20px;
}  
#main .log a,#main .log span{
      color:white;
  }
#main>.log{
    background:black;
    border-radius: 10px;
    
}

#main>.log>.top{
    margin-top:30px;
    margin-left:15px;
}
#main .log .top img{
    width:50px;
    height:50px;
    margin-right:15px;
    vertical-align: middle;
}
#main .log .top span{
    font-size:18px
}

#main .bottom{
    margin-top:35px;
    padding-left:0;
    display:flex;
    justify-content: space-around;

}
#main .bottom>li{
    text-align:center;
}

/*我的订单*/
#main>.myOrder{
    margin-top:30px;
    border-bottom:1px solid rgb(152, 152, 161)
}
/*字体颜色是黑色*/
#main>.myOrder p{
    color:black;
}
#main>.myOrder>p{
    font-size:20px;
}
#main .myOrder ul{
    margin-top:30px;
    margin-bottom:30px;
    padding-left: 0;
    list-style-type: none;
    display:flex;
    justify-content: space-around;
    
}
#main .myOrder ul li{
    text-align:center;
}
#main .myOrder ul li img{
    width:30px;
    height:30px;
}
</style> 
