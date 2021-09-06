<template>
	<view class="desc">
		<view class="top">
			<view class="top-one row">
				<view class="num">
					3597.04
				</view>
				<view>
					<text>高</text>
					<text>3597.37</text>
				</view>
				<view>
					<text>开</text>
					<text>3559.90</text>
				</view>
				<view>
					<text>量</text>
					<text>5.7亿</text>
				</view>
			</view>
			<view class="top-tow row">
				<view>
					<text>+29.94</text>
					<text>+0.84%</text>
				</view>
				<view>
					<text>低</text>
					<text>3557.68</text>
				</view>
				<view>
					<text>换</text>
					<text>1.51%</text>
				</view>
				<view>
					<text>额</text>
					<text>6911亿</text>
				</view>
			</view>
		</view>
		<view class="echarts-view">
			<view class="titel-rpw">
				<view :class="{titel:titels == 0}" @click="chartSwitchover(0)">分时</view>
				<view :class="{titel:titels == 1}" @click="chartSwitchover(1)">日K</view>
				<view :class="{titel:titels == 2}" @click="chartSwitchover(2)">周K</view>
				<view :class="{titel:titels == 3}" @click="chartSwitchover(3)">月K</view>
			</view>
			<view class="echarts-body">
				<fenshiEcharts v-if="echartsShow"></fenshiEcharts>
				<riK v-else></riK>
			</view>
		</view>
		<view class="news">
			<view class="titel">新闻</view>
			<view class="newsLIst">
				<view class="newsItem" v-for=" (item,index) in newsList" :key="index">
					<view class="newTitel">
						{{item.titel}}
					</view>
					<view class="msg">
						<view class="author">
							{{item.author}}
						</view>
						<view class="times">
							{{item.times}}
						</view>
					</view>
				</view>
				<view class="jiaZai">
					加载更多
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import fenshiEcharts from '@/component/fenshi/fenshiEcharts.vue';
	import riK from '@/component/riK/riK.vue';
	export default {
		components: {
			fenshiEcharts,
			riK
		},
		data() {
			return {
				titels: 0,
				echartsShow:true,
				newsList: [{
						titel: "北向资金今日大幅净买入51.37亿元，紫金矿业获净买入11.17亿元",
						author: "同花顺金融研究中心",
						times: "17:30"
					},
					{
						titel: "涨停复盘:顺周期板块应修复风电光伏掀起涨停潮",
						author: "同花顺金融研究中心",
						times: "17:10"
					},
					{
						titel: "工信部与国开行签署战略合作协议",
						author: "证券时报网",
						times: "18:50"
					},
					{
						titel: "商务部:中国海外仓数量已经超过1900个",
						author: "中国新闻网",
						times: "18:49"
					},
					{
						titel: "凌云股份:定增申请获证监会受理",
						author: "同花顺综合",
						times: "18:48"
					}
				],
			}
		},
		methods: {
			chartSwitchover(val) {
				this.titels = val;
				switch (val){
					case 0:
						this.echartsShow=true
						break;
					default:
						this.echartsShow=false
						break;
				}
			}
		}
	}
</script>

<style scoped>
	.desc {
		padding: 0 20rpx;
	}

	.row {
		display: flex;
	}

	.row text {
		margin-right: 10rpx;
	}

	.num {
		font-size: 50rpx;
	}

	.titel-rpw {
		display: flex;
		gap: 50rpx;
	}

	.titel {
		position: relative;
		font-weight: 600;
	}

	.titel::after {
		content: '';
		position: absolute;
		bottom: 0;
		left: 0;
		width: 31px;
		height: 10px;
		z-index: -1;
		background-image: linear-gradient(to right, #f8af8a, #f49998);
	}

	.echarts-body {
		height: 300px;
	}

	.msg {
		display: flex;
		justify-content: space-between;
	}

	.jiaZai {
		text-align: center;
	}
</style>
