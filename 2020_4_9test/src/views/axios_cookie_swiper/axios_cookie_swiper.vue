<template>
    <div class='swiper-container ditle'>  
            <div class='swiper-wrapper'>
                <slot></slot>
            </div>
    </div>
</template>

<script>
// 使用swiper流程
// 加载插件 导入Swiper
// HTML内容 div 模板
// 给Swiper定义一个大小
// 初始化Swiper

import Swiper from 'swiper'
import 'swiper/dist/css/swiper.css'


export default {
    mounted() {
        new Swiper('.ditle',{
            // loop:true,  循环播放
            sildesPerView : 3,
            sapceBetween : 30,
            freeMode: true,
            // 这是分页器的一个初始化，使用时才初始化
            // pagination:{
            //     el: '.swiper-pagination',
            // }
        })
    },
}
</script>

<style lang="scss" scoped>
.swiper-wrapper{
    img{
        width: 100%;
    }
}
</style>