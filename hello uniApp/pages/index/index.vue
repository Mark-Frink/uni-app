<template>
	<view class="content">
		<text class="title">{{ title }}</text>
		<view class="row one">
			<view class="one-left">
				<view class="left-row1">
					<view class="pics"></view>
					<view>已收盘</view>
				</view>
				<view class="left-row2">{{ time }}</view>
			</view>
			<view class="seach">
				<view class="svg">
					<svg xmlns="http://www.w3.org/2000/svg" version="1.1" height="25" width="25">
						<path d="m 19 19 l 5 5" stroke="black" stroke-width="1" fill="none" />
						<g stroke="black" stroke-width="1" fill="black"><circle id="pointA" cx="13" cy="13" stroke="black" fill="none" r="8" /></g>
					</svg>
				</view>
				<view class="texts">搜股票名称/股票代码</view>
			</view>
		</view>
		<view class="row tow">
			<view class="stock-data">
				<navigator url="/pages/desc/desc" hover-class="navigator-hover" class="stock-list" v-for="(item, index) in datalistL" :key="index">
					<view class="stock-item" :class="{ red: item.values.val.includes('+') }">
						<view class="titel">{{ item.name }}</view>
						<view class="money">{{ item.money }}</view>
						<view class="amount">
							<view class="amount-item">{{ item.values.val }}</view>
							<view class="amount-item">{{ item.values.percentage }}</view>
						</view>
					</view>
				</navigator>
			</view>
			<view class="stock-tb">
				<view class="fg blocks"></view>
				<view class="fg cens"></view>
				<view class="fg blocks"></view>
			</view>
		</view>
		<view class="row three">
			<view class="three-list">
				<view class="three-item">
					<text class="titel">同花顺</text>
					<text class="tags iconfont icon-toutiao"></text>
				</view>
				<swiper class="three-item slideshow" :vertical="true" :autoplay="true" :circular="true">
					<swiper-item class="slideshow-item" v-for="(item, index) in slideshowList" :key="index">
						<view class="sli-itm">{{ item }}</view>
					</swiper-item>
				</swiper>
				<view class="three-item"><text class="iconfont icon-xia"></text></view>
			</view>
		</view>
		<view class="row four">
			<view class="plate">
				<view class="titel">
					<view class="pt-lest">今日板块</view>
					<view class="pt-right">查看全部板块</view>
				</view>
				<scroll-view :scroll-x="true" class="plates-list">
					<view class="plate-item">
						<view class="pli-body">
							<view class="pl-tags">热门概念</view>
							<view class="plb-item">
								<view class="tops">
									<view class="names">光伏建筑一体化</view>
									<view class="proportion">6.89%</view>
								</view>
								<view class="bottom">
									<view class="names">汉嘉设计</view>
									<view class="proportion">20.02%</view>
								</view>
							</view>
							<view class="plb-item">
								<view class="tops">
									<view class="names">风电</view>
									<view class="proportion">6.10%</view>
								</view>
								<view class="bottom">
									<view class="names">金盛科技</view>
									<view class="proportion">20.02%</view>
								</view>
							</view>
							<view class="plb-item">
								<view class="tops">
									<view class="names">煤炭概念</view>
									<view class="proportion">5.88%</view>
								</view>
								<view class="bottom">
									<view class="names">安源煤业</view>
									<view class="proportion">10.13%</view>
								</view>
							</view>
						</view>
					</view>
					<view class="plate-item">
						<view class="pli-body">
							<view class="pl-tags">热门行业</view>
							<view class="plb-item">
								<view class="tops">
									<view class="names">光伏建筑一体化</view>
									<view class="proportion">6.89%</view>
								</view>
								<view class="bottom">
									<view class="names">汉嘉设计</view>
									<view class="proportion">20.02%</view>
								</view>
							</view>
							<view class="plb-item">
								<view class="tops">
									<view class="names">风电</view>
									<view class="proportion">6.10%</view>
								</view>
								<view class="bottom">
									<view class="names">金盛科技</view>
									<view class="proportion">20.02%</view>
								</view>
							</view>
							<view class="plb-item">
								<view class="tops">
									<view class="names">煤炭概念</view>
									<view class="proportion">5.88%</view>
								</view>
								<view class="bottom">
									<view class="names">安源煤业</view>
									<view class="proportion">10.13%</view>
								</view>
							</view>
						</view>
					</view>
					<view class="plate-item">
						<view class="pli-body">
							<view class="pl-tags">热门概念</view>
							<view class="plb-item">
								<view class="tops">
									<view class="names">光伏建筑一体化</view>
									<view class="proportion">6.89%</view>
								</view>
								<view class="bottom">
									<view class="names">汉嘉设计</view>
									<view class="proportion">20.02%</view>
								</view>
							</view>
							<view class="plb-item">
								<view class="tops">
									<view class="names">风电</view>
									<view class="proportion">6.10%</view>
								</view>
								<view class="bottom">
									<view class="names">金盛科技</view>
									<view class="proportion">20.02%</view>
								</view>
							</view>
							<view class="plb-item">
								<view class="tops">
									<view class="names">煤炭概念</view>
									<view class="proportion">5.88%</view>
								</view>
								<view class="bottom">
									<view class="names">安源煤业</view>
									<view class="proportion">10.13%</view>
								</view>
							</view>
						</view>
					</view>
				</scroll-view>
			</view>
		</view>
		<view class="row five">
			<view class="titel">股票排行</view>
			<view class="seniority">
				<view>涨幅榜</view>
				<view>跌幅榜</view>
				<view>成交额</view>
				<view>涨速榜</view>
			</view>
			<view class="table">
				<view class="thead">
					<view class="th">股票名称</view>
					<view class="th">最新价</view>
					<view class="th">涨跌幅</view>
					<view class="th">涨速</view>
				</view>
				<view class="tbody">
					<view class="tr" v-for="(item, index) in seniority" :key="index">
						<view class="td">
							<view>{{ item.name }}</view>
							<view>{{ item.id }}</view>
						</view>
						<view class="td">{{ item.price }}</view>
						<view class="td">{{ item.percentage }}</view>
						<view class="td">{{ item.speed }}</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			title: '登录',
			time: '',
			datalistL: [
				{
					name: '上证指数',
					money: 3567.1,
					values: {
						val: '+23.16',
						percentage: '+0.65%'
					}
				},
				{
					name: '深证成指',
					money: 14314.09,
					values: {
						val: '-14.29',
						percentage: '-0.10%'
					}
				},
				{
					name: '创业扳指',
					money: 3186.85,
					values: {
						val: '-27.27',
						percentage: '-0.85%'
					}
				}
			],
			slideshowList: ['炒作中国企业监管措施!外媒:美众院将讨论在美上市中企“风险”', '对话陈东升：我奉行专业主义 专业代表效率'],
			seniority: [
				{
					name: '宏微科技',
					id: 688711,
					price: '101.06',
					percentage: '+31.42%',
					speed: '+0.06%'
				},
				{
					name: '金盘科技',
					id: 688676,
					price: '23.62',
					percentage: '+20.02%',
					speed: '+0.00%'
				},
				{
					name: '海联讯',
					id: 300277,
					price: '10.25',
					percentage: '+20.02%',
					speed: '+0.00%'
				},
				{
					name: '力星股份',
					id: 300421,
					price: '25.48',
					percentage: '+20.02%',
					speed: '+0.00%'
				},
				{
					name: '汉嘉设计',
					id: 300746,
					price: '15.35',
					percentage: '+20.02%',
					speed: '+0.00%'
				},
				{
					name: '汉嘉设计',
					id: 300746,
					price: '15.35',
					percentage: '+20.02%',
					speed: '+0.00%'
				},
				{
					name: '汉嘉设计',
					id: 300746,
					price: '15.35',
					percentage: '+20.02%',
					speed: '+0.00%'
				},
				{
					name: '汉嘉设计',
					id: 300746,
					price: '15.35',
					percentage: '+20.02%',
					speed: '+0.00%'
				},
				{
					name: '汉嘉设计',
					id: 300746,
					price: '15.35',
					percentage: '+20.02%',
					speed: '+0.00%'
				},
				{
					name: '汉嘉设计',
					id: 300746,
					price: '15.35',
					percentage: '+20.02%',
					speed: '+0.00%'
				},
				{
					name: '中环海陆',
					id: 301040,
					price: '39.28',
					percentage: '+20.01%',
					speed: '+0.00%'
				},
				{
					name: '四方达',
					id: 300179,
					price: '11.16',
					percentage: '+20.00%',
					speed: '+0.00%'
				}
			]
		};
	},
	onLoad() {
		let datas = new Date();
		let year = datas.getFullYear();
		let month = datas.getMonth() + 1;
		let day = datas.getDate();
		let week = datas.getDay();
		month < 10 ? (month = `0${month}`) : (month = `month`);
		day < 10 ? (day = `0${day}`) : (day = `day`);
		switch (week) {
			case 1:
				week = '一';
				break;
			case 2:
				week = '二';
				break;
			case 3:
				week = '三';
				break;
			case 4:
				week = '四';
				break;
			case 5:
				week = '五';
				break;
			case 6:
				week = '六';
				break;
			default:
				week = '日';
				break;
		}
		this.time = `${year}年${month}月${day}日 星期${week}`;
	},
	methods: {}
};
</script>

<style scoped>
.row {
	display: flex;
	padding: 10rpx 36rpx;
}
.one {
	justify-content: space-between;
	align-items: center;
}
.title {
	font-size: 34rpx;
	color: #000;
	position: fixed;
	top: 9px;
	left: 15px;
	z-index: 999;
}
.left-row1 {
	font-size: 50rpx;
	font-weight: 600;
	display: flex;
	align-items: center;
	gap: 10rpx;
	letter-spacing: 2px;
}
.pics {
	background-image: linear-gradient(to bottom right, #ac20fa, #684bdc);
	width: 52rpx;
	height: 52rpx;
	position: relative;
	border-radius: 5px;
}
.pics::after {
	content: '';
	width: 32rpx;
	height: 32rpx;
	border-radius: 50%;
	border: #fffffff0 2px solid;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
}
.pics::before {
	content: '';
	width: 18rpx;
	height: 18rpx;
	background: #fffffff0;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
}
.left-row2 {
	font-size: 16rpx;
}
.seach {
	display: flex;
	gap: 10rpx;
	align-items: center;
	box-shadow: #c0c0c0 0 0 2px 1px;
	border-radius: 30px;
	height: 30px;
	padding: 0 20rpx;
	font-size: 16rpx;
}
.tow {
	flex-direction: column;
	margin: 20rpx 0;
}
.stock-data,
.amount {
	display: flex;
	justify-content: space-between;
}
.stock-item {
	color: #fff;
	background-image: linear-gradient(to right, #f26213, #e9332e);
	text-align: center;
	padding: 10rpx 20rpx;
	gap: 10rpx;
	width: 220rpx;
	border-radius: 20rpx;
	box-sizing: border-box;
}
.stock-item:not(.red) {
	background-image: linear-gradient(to right, #5fbf0f, #039a01);
}
.money {
	font-size: 40rpx;
}
.amount {
	font-size: 24rpx;
}
.stock-tb {
	display: flex;
	height: 20rpx;
	margin: 40rpx 0;
}
.fg {
	position: relative;
}
.blocks {
	flex: 1;
}
.blocks:first-child {
	border-radius: 3px 0 0 3px;
	background-image: linear-gradient(to right, #5fbf0f, #039a01);
}
.blocks:last-child {
	border-radius: 0 3px 3px 0;
	background-image: linear-gradient(to right, #f26213, #e9332e);
}
.blocks:first-child::after {
	content: '跌 2136家';
	position: absolute;
	left: 0;
	top: 24rpx;
	font-size: 20rpx;
}
.blocks:last-child::after {
	content: '涨 2223家';
	position: absolute;
	right: 0;
	top: 24rpx;
	font-size: 20rpx;
}
.cens {
	transform: skewX(-30deg) translateX(-50%);
	background-color: #666666;
	width: 60rpx;
	height: 20rpx;
	position: absolute;
	left: 50%;
	z-index: 5;
}
.cens::after,
.cens::before {
	content: '';
	background-color: #fff;
	width: 10rpx;
	height: 20rpx;
	position: absolute;
}
.cens::after {
	right: 0;
}
.three {
	display: block;
	margin: 40rpx 0;
}
.three-list {
	display: flex;
	justify-content: space-between;
	align-items: center;
	border-radius: 6px;
	box-shadow: 0 0 5px #e3e3e3;
	padding: 10rpx;
}
.three-item {
	flex-shrink: 0;
}
.three-item:first-child {
	color: #e93030;
	font-style: italic;
	line-height: 1;
	position: relative;
	width: 80px;
}
.titel {
	font-weight: 600;
}
.tags {
	margin-left: 10rpx;
	font-size: 48rpx;
	position: relative;
	right: -3px;
	top: 3px;
}
.slideshow {
	flex: 1 1 0%;
	font-size: 26rpx;
	box-sizing: border-box;
	padding: 0 10px;
	height: 30px;
	line-height: 30px;
}
.slideshow-item {
	height: 30px !important;
	line-height: 30px;
}
.sli-itm {
	overflow: hidden;
	text-overflow: ellipsis;
	white-space: nowrap;
	width: 220px;
}
.icon-xia {
	font-size: 20rpx;
}
.four {
	display: block;
}
.plate .titel {
	display: flex;
	justify-content: space-between;
	margin: 10px 0;
}
.pt-lest {
	font-size: 40rpx;
}
.pt-right {
	color: #999999;
	font-weight: 400;
}
.plates-list {
	white-space: nowrap;
}
.plate-item {
	display: inline-block;
	padding: 5px;
}
.plate-item:nth-child(2) {
	margin: 0 10px;
}
.pli-body {
	display: flex;
	box-shadow: #e9e9e9 0 0 5px;
	border-radius: 10px;
	position: relative;
}
.pl-tags {
	background-image: linear-gradient(to right, #f26014, #ea352e);
	border-radius: 10px 0;
	padding: 3px 6px;
	font-size: 10px;
	color: #fff;
	position: absolute;
	top: 0;
	left: 0;
}
.plb-item {
	text-align: center;
	color: #666;
	position: relative;
	padding: 30px 5px 5px 5px;
}
.plb-item::after {
	content: '';
	width: 1px;
	height: 80px;
	background-color: #ededed;
	position: absolute;
	top: 20px;
	right: 0;
}
.plb-item:last-child::after {
	background-color: #00000000;
}
.tops {
	font-size: 14px;
	margin: 0 0 20rpx;
}
.bottom {
	font-size: 12px;
}
.tops .proportion {
	font-weight: 550;
}
.proportion {
	color: #ea4646;
}
.five {
	display: block;
	margin-top: 20px;
}
.five .titel {
	font-size: 40rpx;
}
.seniority {
	display: flex;
	gap: 10px;
}
.seniority view:first-child {
	font-weight: 600;
	font-size: 36rpx;
	position: relative;
}
.seniority view:first-child::after {
	content: '';
	position: absolute;
	bottom: 0;
	left: 0;
	width: 55px;
	height: 10px;
	z-index: -1;
	background-image: linear-gradient(to right, #f8af8a, #f49998);
}
.tr,
.thead {
	display: flex;
	gap: 10rpx;
}
.tr,
.seniority {
	margin: 20rpx 0;
}
.td,
.th {
	width: 80px;
	text-align: center;
	flex-shrink: 0;
	position: relative;
}
.th {
	font-size: 12px;
	color: #999999;
}
.th:nth-child(3)::before,
.th:nth-child(3)::after {
	content: '';
	border: #e93030 5px solid;
	position: absolute;
	width: 0;
	height: 0;
	right: 10px;
}
.th:nth-child(3)::before {
	border-color: #00000000 #00000000 #e93030 #00000000;
	top: -2px;
}
.td:nth-child(2),
.td:nth-child(3) {
	color: #ea4646;
	font-weight: 600;
}
.td:nth-child(4) {
	font-weight: 600;
}
.th:nth-child(3)::after {
	border-color: #ededed #00000000 #00000000 #00000000;
	top: 10px;
}
.td:first-child,
.th:first-child {
	flex: 1;
	text-align: left;
}
.td:first-child view:last-child {
	font-size: 12px;
}
</style>
