<template>
	<div>
		<HomeHeader></HomeHeader>
		<HomeSwiper :list="swiperList"></HomeSwiper>
		<HomeIcons :list="iconList"></HomeIcons>
		<HomeRecommend :list="recommendList"></HomeRecommend>
		<HomeWeekend :list="weekendList"></HomeWeekend>
	</div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
export default {
	name:'Home',
	components:{
		HomeHeader,
		HomeSwiper,
		HomeIcons,
		HomeRecommend,
		HomeWeekend,
	},
	data () {
		return {
			SwiperList: [],
			iconList: [],
			recommendList: [],
			weekendList: []
		}
	},
	methods:{
		getHomeInfo () {
			axios.get('/api/index.json')
			.then(this.getHomeInfoSucc)
			
//			let _this = this;
//			axios.get('/api/index.json')
//			.then((res) => {
//				_this.getHomeInfoSucc(res)
//			})
		},
		getHomeInfoSucc (res) {
			res = res.data
			if (res.ret && res.data) {
				const data = res.data
				this.swiperList = data.swiperList
				this.iconList = data.iconList
				this.recommendList = data.recommendList
				this.weekendList = data.weekendList
			}
		}
	},
	mounted () {
		this.getHomeInfo()
	}
	
}
</script>

<style>
	
</style>