<template>
	<div class="icons">
		<swiper :options="swiperOption">
        <swiper-slide v-for="(page, index) of pages" :key="index">
		     <div class="icon" v-for="item of page" :key="item.id">
		     	<div class="icon-img">
				    <img class="icon-img-content" :src="item.imgUrl"/>
			    </div>
			    <p class="icon-desc">{{item.desc}}</p>
		     </div>
		</swiper-slide>
	    </swiper>
	</div>
</template>

<script>
export default {
	name: 'HomeIcons',
	props: {
		list: Array
	},
	data:function(){
		return {
			swiperOption: {
				autoplay:false
			}
		}
	},
	computed:{
		pages () {
			const pages = []
			this.list.forEach((item, index) => {
				const page = Math.floor(index / 8)
				if (!pages[page]) {
					pages[page] = []
				}
				pages[page].push(item)
			})
			return pages
		}
	}
}
</script>

<style lang="stylus" scoped>
.icons .swiper-container{

	height: 0;
	padding-bottom: 50%;
}
.icons{
	margin-top: .1rem;
}
.icons .icon{
	position: relative;
	overflow: hidden;
	float: left;
	width: 25%;
	height: 0;
	padding-bottom: 25%;
}
.icons .icon .icon-img{
	position: absolute;
	top:0;
	left: 0;
	right: 0;
	bottom: .44rem;
	box-sizing: border-box;
	padding: .1rem;
}
.icon-img-content{
	height: 100%;
	display: block;
    margin: 0 auto;
    margin-top: .1rem;
}
.icon-desc{
	position: absolute;
	bottom:0;
	left: 0;
	right: 0;
	line-height: .44rem;
	height: .44rem;
	color: #333;
	text-align: center;
	overflow: hidden;
	white-space: nowrap;
	text-overflow: ellipsis;
}
</style>