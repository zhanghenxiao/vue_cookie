<template>
    <div>this page is axios_cookie.vue 
        <hr>
        <ul>
            <li v-for="data in datalist" :key="data">
                <h3>{{data.nm}}</h3>
                <!-- <img :src= "data.img | cookiefilter"/> --> 
                <!-- <img :src= "imglist(data.img)"/> -->
                <axios_cookie_swiper>
                    <img :src= "imglist(data.img)"/>
                </axios_cookie_swiper>
                
            </li>
        </ul>
        
    </div>
</template>

<script>
import axios from 'axios'
import axios_cookie_swiper from  './axios_cookie_swiper/axios_cookie_swiper'


// Vue.filter("cookiefilter",function(cookiepath){
//     return cookiepath.replace('w.h','128.180')
// })
export default {
    data(){
        return{
             datalist: ""
        }
    },
    mounted() {
    // mounted 是vue 生命周期中都会执行的一个步骤

        // 此出应使用过滤器 vue.filter
        //在网上真实渲染数据https://p1.meituan.net/170.230/movie/a19913517ec4dd7b1e8c56a199ceaa4280560.jpg
        //实际请求数据 http://p0.meituan.net/w.h/movie/07e0ee6c6f30700e6d4ab6774d95fc4f108727.jpg
        axios.get("/ajax/mostExpected?ci=55&limit=10&offset=0&token=").then(res=>{
            console.log(res.data);
            console.log("猫眼");
            console.log(res.data.coming.length) //获取对象长度
            // this.datalist = (res.data.coming[0].img)
            this.datalist =  res.data.coming
        })
    },
    methods: {
       imglist(path){
           return path.replace('w.h','128.180')
       } 
    },
    components:{
        axios_cookie_swiper
    }
    
}
</script>

<style lang="scss" scoped>
    h3{
      background-color:beige;
    }
    // div{
    //    background-color: violet;
    // }
</style>

