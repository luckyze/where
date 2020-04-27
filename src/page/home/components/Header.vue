<template>
	<div class="header">
		<div class="header-left">
			<div class="iconfont back-icon">&#xe624;</div>
		</div>
		<div class="header-input"><span class="iconfont search-icon">&#xe632;</span>输入城市/景点/游玩主题</div>
		<router-link to='/City'>
			<div class="header-right">{{this.city}}
			    <span class="iconfont arrow-icon">&#xe64a;</span>
			</div>
		</router-link>
	</div>
</template>

<script>
import { mapState } from 'vuex'
export default {
	name:'HomeHeader',
    computed: {
    	...mapState(['city'])
    }
}
</script>

<style lang="stylus" scoped>
  /*1rem = html font-size=50px*/
  .header {
    display: flex;
    line-height: .86rem;
    background: #00bcd4;
    color: #fff;
    height: .86rem
  }

  .header-left {
  	text-align: center;
    width: 0.64rem;
    float: left
  }
.header-left .back-icon{
	text-align: center;
	font-size: .4rem;
}
  .header-input {
    flex: 1;
    height: 0.64rem;
    line-height: 0.64rem;
    margin-top: 0.12rem;
    margin-left: 0.2rem;
    padding-left: 0.1rem;
    background: #ffffff;
    border-radius: 0.1rem;
    color: #ccc
  }
  .header-input .search-icon{
  	margin-right: .1rem;
  }

  .header-right {
  	text-align: center;
    min-width: 1.04rem;
    padding: 0 .1rem;
    float: right;
    color: #ffffff;
  }
  .header-right .arrow-icon{
  	font-size: .24rem;
  }
</style>