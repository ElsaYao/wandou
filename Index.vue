<template>
    
    <div id="homepage-app">
       <my-header></my-header>
       <div class="top-img">
         <div>
            <img src="http://127.0.0.1:3000/homepage-img/tou1.webp" alt="">
         </div>
         <div>
            <img src="http://127.0.0.1:3000/homepage-img/tou2.webp" alt="">
         </div>
         <div>
             <img src="http://127.0.0.1:3000/homepage-img/toudong.gif" alt="">
         </div>
         <div>
             <img src="http://127.0.0.1:3000/homepage-img/toudong2.gif" alt="">
         </div> 
         <div>
             <img src="http://127.0.0.1:3000/homepage-img/pink2.webp" alt="">
         </div> 
       </div>
       <div class="go3">
           <router-link to=""><img src="http://127.0.0.1:3000/homepage-img/manjianquan.webp" alt=""></router-link>
           <router-link to=""><img src="http://127.0.0.1:3000/homepage-img/dapaizhijiang.webp" alt=""></router-link>
           <router-link to=""><img src="http://127.0.0.1:3000/homepage-img/zuheliangban2.webp" alt=""></router-link>
       </div>
       <div class="slide-product">
           <div class="slide"  v-for="(item,i) of  productList" :key="i">
                <div class="top">
                    <div class="image">
                        <img :src="`http://127.0.0.1:3000/homepage-img/`+item.pic1" alt="">
                        <img :src="`http://127.0.0.1:3000/homepage-img/`+item.pic2" alt="">
                        <img :src="`http://127.0.0.1:3000/homepage-img/`+item.pic3" alt="">
                    </div>
                    <div class="text">
                        <p>{{item.title}}</p>
                        <p>￥{{item.price}}</p>
                    </div>
                    
                </div>
                <div class="bottom">
                   <span>加入购物袋</span>
                   <img src="http://127.0.0.1:3000/homepage-img/gouwudai.png" alt="">
                </div>
           </div>
       </div>
       <div class="fuli">
        <div >	
            <div>
                <img src="http://127.0.0.1:3000/homepage-img/yinghuafuli.webp" alt="" width="100%"/>
            </div>
            <div >
                <img src="http://127.0.0.1:3000/homepage-img/yinghuadazuozhan.webp" alt="" width="100%"/>
            </div>
            <div>
                <img src="http://127.0.0.1:3000/homepage-img/qianwanshenquan.gif" alt="" width="100%"/>
            </div>
		</div>
       </div>
       <!-- 秒杀 -->
       <div class="lightningDeal">
          <div class="top">
            <p>今日秒杀</p>
            <p>距离结束还有{{h}}:{{m}}:{{s}}</p>
          </div>
          <div class="content" >
             <div v-for="(item,i) of  lightningList" :key="i">
                  <img :src="`http://127.0.0.1:3000/homepage-img/`+item.pic" alt="" style="width:100px;height:100px">
                  <div>
                      <span>{{item.lightningPrice}}</span>
                      
                      <span style="display:inline-block;margin-left:5px">{{item.price}}</span>
                      <span style= "display:inline-block;margin-left:-25px; font-size:23px" >一</span>
                  </div>
                  <div>
                      <p>{{item.title}}</p>
                  </div>
              </div>
          </div>
       </div>
       <!-- 药妆店 -->
       <div class="mui-card">
        <div class="mui-card-header">药妆店</div>
        <div class="mui-card-content">
            <div >
                <img src="http://127.0.0.1:3000/homepage-img/yao2.webp" alt="">
            </div>
        </div>
        <div></div>
       </div> 
    </div>   
</template>
<script>
//1. 先引入header.vue组件对象，临时命名为myHeader，将来组件标签就是<my-header>
import myHeader from "@/components/header.vue"
//引入nav-bar

export default {
    data(){
        return{
          productList:[],
        //3个秒杀产品列表  
        lightningList:[],
        h:0,
        m:0,
        s:0
        }
    },
    created(){
       this.loadProducts();
       this.lightning();
       
       
    },
    updated(){
    }, 
    methods:{
        //请求商品数据
    loadProducts(){
       var url="http://127.0.0.1:3000/IndexProducts"
       //发送ajax请求
       this.axios.get(url).then(result=>{
           this.productList=result.data;
           console.log(this.productList);
        //    让产品标题显示为字符串+...的格式
        for(var item of this.productList){
            if(item.title.length>20){
                item.title=item.title.substr(0,11)+"..."
            }
        }

       })
    }, 
    lightning(){
        var url="http://127.0.0.1:3000/lightningDeal";
        //发送ajax请求
         this.axios.get(url).then(result=>{
           this.lightningList=result.data;
           console.log(this.lightningList);
        //    让产品标题显示为字符串+...的格式
        for(var item of this.lightningList){
            if(item.title.length>8){
                item.title=item.title.substr(0,5)+"..."
            }
        }

       })
    },
    // 倒计时函数
    djs(){
         //设置h,数值为24(一天24小时)减去当前的小时,下述m与s同理
       this.h = 23 - (new Date().getHours())
     
       this.m = 59 - (new Date().getMinutes())
     
        this.s = 59 - (new Date().getSeconds())
        
        },
     
       
    },
    //2. 将header.vue设置为当前组件的子组件
    components:{
      myHeader
    }
}
</script>
<style scoped>
#homepage-app{
    background:url("http://127.0.0.1:3000/homepage-img/pink.webp");
    background-repeat:no-repeat;
    background-size:cover;
   
}
#homepage-app>.top-img{
    margin-top:84px;
}
#homepage-app>.top-img>div>img{
    width:100%;
    margin:0;
}
#homepage-app>.top-img>div{
    margin-top:-5.5px;
}
#homepage-app>.top-img>div:first-child{
    margin-top:0;
}

/* 三个go */
#homepage-app>.go3{
    display:flex;
}
#homepage-app>.go3 a{
    margin-top:-5px;
    width:38%
}
#homepage-app>.go3 a img{
    width:100%;
}

/* 滑动产品样式 */
#homepage-app>.slide-product{
   padding:15px;
    width:100%;
    display:flex;
    white-space:nowrap; 
    overflow-x:auto;
    
}
/* 去掉滚动条 */
::-webkit-scrollbar{
  display:none
}
#homepage-app>.slide-product>.slide{
    background:rgb(245, 241, 241);
    width:200px;
    text-align:center;
    border-radius:10px;
    margin-left:3%;
    padding:0 2px
   

}
#homepage-app>.slide-product>.slide:first-child{
    margin-left:0;
}
#homepage-app>.slide-product>.slide>.top>.image>img{
    display:block;
}
#homepage-app>.slide-product>.slide>.top>.image img:first-child{
   margin-left:54px;
}
#homepage-app>.slide-product>.slide>.top>.image img:nth-child(2){
    margin:0 auto;
    margin-top:-25%;
    width:90%;
}
#homepage-app>.slide-product>.slide>.top>.image img:nth-child(3){
    width:35%;
    margin-top:-50%;
    margin-left:2px;
}
#homepage-app>.slide-product>.slide>.top>.text{
    
     margin-top:30%
}
#homepage-app>.slide-product>.slide>.top>.text p:first-child{
    height:50px;
    text-align: center;
    white-space:normal;  
    font-size:14px;
    color:#000;
}
#homepage-app>.slide-product>.slide>.top>.text p:last-child{
   color:red;
}
#homepage-app>.slide-product>.slide>.bottom{
    border-radius:0 0 10px 10px;
    background:#fff;
    font-size:13px;
}
#homepage-app>.slide-product>.slide>.bottom>img{
    width:12px;
    height:12px;
    margin-left:4px;
    vertical-align: middle;
}
/* 樱花福利三张图片 */
.box-shadow{
    box-shadow:none;
}

/*秒杀样式*/
#homepage-app .lightningDeal{
    padding:0 15px;
    margin-top:20px;
}
#homepage-app .lightningDeal .top{
   display:flex;
   justify-content: space-between;
  
   
}
#homepage-app .lightningDeal .top p{
    color:black;
    font-size:18px;
    font-weight: bold;
}
#homepage-app .lightningDeal .content{
   
    border-radius: 10px;
    border:1px solid rgba(230,230,230,.5);
    background: #fce7e7;
    overflow:hidden;
}
#homepage-app .lightningDeal .content>div{
    float:left; 
    width:110px; 
    text-align:center; 
}



</style>


