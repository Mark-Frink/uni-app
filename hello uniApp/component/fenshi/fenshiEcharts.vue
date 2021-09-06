<template>
	<view class="viewimg">
		<echarts :option="option" style="height: 300px;"></echarts>
	</view>
</template>

<script>
	import echarts from '@/component/echarts/echarts.vue';
	export default {
		data() {
			return{
				timeQuantum:["09:30:00","09:30:10","09:30:20","09:30:30","09:30:40","09:30:50","09:31:00","09:31:10","09:31:20","09:31:30","09:31:40","09:31:50","09:32:00","09:32:10",],
				valueONe:[300,235,415,466,285,415,832,423,163,415,513,246,415,123],
				valueTow:[235,115,285,163,300,466,415,435,812,423,454,513,246,321],
				valueThree:[30,25,41,66,28,45,82,23,63,15,53,26,51,13],
				valueFour:[25,15,85,63,30,46,45,35,12,42,44,53,26,31],
				option:{},
				entTime:""
			}
		},
		components: {
			echarts
		},
		mounted() {
			this.logstatrt();
			setInterval(()=>{
				let a = this.timeToSec(this.entTime);
				let b=this.times(a+10)
				this.timeQuantum.push(b)
				this.valueONe.push(this.randomNumber(3))
				this.valueTow.push(this.randomNumber(3))
				this.valueThree.push(this.randomNumber(2))
				this.valueFour.push(this.randomNumber(2))
				this.entTime=b
				console.log(b);
			},2000)
		},
		methods: {
			//时分秒转时间戳
			timeToSec(time) {
				if (time !== null) {
				　　let s = "";
				　　let hour = time.split(":")[0];
				　　let min = time.split(":")[1];
				　　let sec = time.split(":")[2];
				　　s = Number(hour * 3600) + Number(min * 60) + Number(sec);
				　　return s;
				}
			},
			//时间戳转时分秒
			times(data) {
				let time = Number(data);
				let h = Math.floor(time / 3600);
				let m = Math.floor((time % 3600) / 60);
				let s = parseInt(time % 3600) % 60;
				let hh = h < 10 ? "0" + h : h;
				let mm = m < 10 ? "0" + m : m;
				let ss = s < 10 ? "0" + s : s;
				return hh + ":" + mm + ":" + ss;
			},
			randomNumber(n){
				let rand;
					if(n==2){
						rand = Math.floor(Math.random () * 90) + 10;
					}else if(n==3){
						rand = Math.floor(Math.random () * 900) + 100;
					}
				console.log(rand);
				return rand
			},
			logstatrt() {
				uni.request({
				    url: 'static/json/fenshi.json', //仅为示例，并非真实接口地址。
				    success: (res) => {
							res.data.xAxis.map((val)=>{
								val.data = this.timeQuantum
							});
							res.data.series.forEach((val,index)=>{
								switch (index){
									case 0:
										val.data= this.valueONe
										break;
									case 1:
										val.data= this.valueTow
										break;
									case 2:
										val.data= this.valueThree
										break;
									default:
										val.data= this.valueFour
										break;
								}
							})
								this.option = res.data;
								console.log(this.option);
								this.entTime =this.timeQuantum[this.timeQuantum.length-1]
								console.log(this.entTime);
				    }
				});
			},
		}
	}
</script>

<style scoped>
	.viewimg{
		height: 100%;
	}
</style>
