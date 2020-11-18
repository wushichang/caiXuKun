<template>
	<view class="alphabet">
		<view 
		class="initial" 
		v-for="city in cities" 
		:key="city.initial" 
		@click="click(city.initial)"
		hover-class="hoverClass"
		@touchstart="touchstart"
		@touchmove="touchmove"
		@touchend="touchend">
			{{city.initial}}
		</view>
	</view>
</template>

<script>
	var timer = null;
	export default{
		props: ['cities'],
		data(){
			return {
				touchFlag: false
			}
		},
		methods: {
			click(initial){
				this.$emit('clickInitial',initial);
			},
			touchstart(e){
				// console.log('touchStart',e);
				this.touchFlag = true;
			},
			touchmove(e){
				clearTimeout(timer);
				timer = setTimeout(()=>{
					if(this.touchFlag){
						const initialIndex = Math.floor((e.changedTouches[0].pageY-150)/16);
						if(initialIndex >= 0 && initialIndex < this.cities.length){
							this.$emit('clickInitial',this.cities[initialIndex].initial);
						}
					}
				},30)
				
				
			},
			touchend(e){
				// console.log('touchend',e);
				this.touchFlag = false;
			}
		}
			
	}
</script>

<style>
	.hoverClass {
		font-size: 15px;
	}
	
	.alphabet {
		position: fixed;
		right: 0;
		top: 150px;
		color: #FFFFFF;
		font-size: 10px;
	}
	
	.initial {
		width: 24px;
		line-height: 16px;
		text-align: center;
	}
	
</style>
