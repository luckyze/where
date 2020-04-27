<template>
	<div class="wrapper">
	  <swiper :options="swiperOption" v-if="list.length">
	    <!-- slides -->
	    <swiper-slide v-for="item of list" :key="item.id">
	    	<img class="swiper-img" :src="item.imgUrl" />
	    </swiper-slide>
	    <!-- Optional controls -->
	    <div class="swiper-pagination"  slot="pagination"></div>
	  </swiper>
    </div>
</template>

<script>
export default{
	name: 'HomeSwiper',
	props: {
		list: Array
	},
	data:function() {
		return {
			swiperOption:{
				pagination: '.swiper-pagination',
				loop:true,
				autuPlay:false
			}
		}
	},
	computed: {
		showSwiper() {
			return this.list.length
		}
	}
}
</script>

<style lang="stylus" scoped>
.wrapper >>> .swiper-pagination-bullet-active{
	background: #ffffff;
}
.wrapper{
	width: 100%;
	height: 0;
	overflow: hidden;
	padding-bottom:41%;
	background: #eee;
}
.swiper-img{
	width: 100%;
	height: 3.2rem;
}
</style>