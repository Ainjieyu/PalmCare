<template>
	<view class="">
		<!-- 顶部个人信息 -->
		<view class="bg-gray">
			<view class="flex padding">
				<view class="padding-lr-xs">
					<view class="cu-avatar lg round"
						style="background-image:url(https://image.meiye.art/Fha6tqRTIwHtlLW3xuZBJj8ZXSX3?imageMogr2/thumbnail/450x/interlace/1);">
					</view>
				</view>
				<view class="padding-xs text-xl text-black">
					<view>xxx</view>
					<view class="cu-tag round line-green sm">12890998</view>
				</view>
			</view>
		</view>
		<!-- 基本数据 -->
		<view class="cu-list bg-gray grid col-4 no-border padding-lr-xs radius-lg-bottom">
			<view class="cu-item bg-gray">
				<view class="text-black text-bold text-xxl">
					6
				</view>
				<text>优惠券</text>
			</view>
			<view class="cu-item bg-gray">
				<view class="text-black text-bold text-xxl">
					0
				</view>
				<text>权益卡</text>
			</view>
			<view class="cu-item bg-gray">
				<view class="text-black text-bold text-xxl">
					4
				</view>
				<text>保修卡</text>
			</view>
			<view class="cu-item bg-gray">
				<view class="text-black text-bold text-xxl">
					11
				</view>
				<text>收据</text>
			</view>
		</view>

		<view class="list">
			<view class="li " @tap="dropdown(0)" hover-class="hover">
				<view class="label">
					<view class="icon">
						<image src="../../static/HM-PersonalCenter/sever/point.png"></image>
					</view>
					<view class="text">基本信息</view>
					<image class="to" src="../../static/HM-PersonalCenter/drop.png"></image>

				</view>
				<view class="line" v-if="showdrop0"></view>
				<view class="info bg-gray" v-if="showdrop0">
					<text class="text-bold">工号：</text> 12344<text class="text-bold">姓名：</text>卢丹 <text
						class="text-bold">性别：</text> <text>女\n\n</text>
					<text class="text-bold">护士层级：</text> 事业编制 <text class="text-bold">护理单元：</text>感染科病区
				</view>
			</view>
			<view class="li " @tap="dropdown(1)" hover-class="hover">
				<view class="label">
					<view class="icon">
						<image src="../../static/HM-PersonalCenter/sever/momey.png"></image>
					</view>
					<view class="text">职务变动</view>
					<image class="to" src="../../static/HM-PersonalCenter/drop.png"></image>

				</view>
				<view class="line" v-if="showdrop1"></view>
				<view class="info bg-gray" v-if="showdrop1">
					<table>
						<tr class="table-row">
							<th>职务名称</th>
							<th v-for="item in PositionList" :key="item.PositionTime">{{item.PositionName}}</th>

						</tr>
						<tr class="table-row">
							<td>行政职务</td>
							<td v-for="item in PositionList" :key="item.PositionTime">{{item.PositionJob}}</td>
						</tr>
						<tr class="table-row">
							<td>任命时间</td>
							<td v-for="item in PositionList" :key="item.PositionTime">{{item.PositionTime}}</td>
						</tr>
					</table>
				</view>
			</view>
			<view class="li " @tap="dropdown(2)" hover-class="hover">
				<view class="label">
					<view class="icon">
						<image src="../../static/HM-PersonalCenter/sever/quan.png"></image>
					</view>
					<view class="text">职称变动</view>
					<image class="to" src="../../static/HM-PersonalCenter/drop.png"></image>

				</view>
				<view class="line" v-if="showdrop2"></view>
				<view class="info  bg-gray" v-if="showdrop2">
					<table>
						<tr class="table-row2">
							<th>资格名称</th>
							<th v-for="item in professionalList" :key="item.professionalTime">{{item.professionalName}}</th>
						</tr>
						<tr class="table-row2">
							<td>资格获得时间</td>
							<td v-for="item in professionalList" :key="item.professionalTime">{{item.professionalGetTime}}</td>
						</tr>
						<tr class="table-row2">
							<td>聘任职称</td>
							<td v-for="item in professionalList" :key="item.professionalTime">{{item.professionalJob}}</td>
						</tr>
						<tr class="table-row2">
							<td>聘任时间</td>
							<td v-for="item in professionalList" :key="item.professionalTime">{{item.professionalTime}}</td>
						</tr>
					</table>
				</view>
			</view>
			<view class="li " @tap="dropdown(3)" hover-class="hover">
				<view class="label">
					<view class="icon">
						<image src="../../static/HM-PersonalCenter/sever/renw.png"></image>
					</view>
					<view class="text">教育经历</view>
					<image class="to" src="../../static/HM-PersonalCenter/drop.png"></image>

				</view>
				<view class="line" v-if="showdrop3"></view>
				<view class="info  bg-gray" v-if="showdrop3">
				</view>
			</view>

			<view class="li noborder" @tap="dropdown(4)" v-bind:class="{'noborder':li_i==0}" hover-class="hover">
				<view class="label">
					<view class="icon">
						<image src="../../static/HM-PersonalCenter/sever/bank.png"></image>
					</view>
					<view class="text">工作经历</view>
					<image class="to" src="../../static/HM-PersonalCenter/drop.png"></image>

				</view>
				<view class="line" v-if="showdrop4"></view>
				<view class="info  bg-gray" v-if="showdrop4">
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
				showdrop0: false,
				showdrop1: false,
				showdrop2: false,
				showdrop3: false,
				showdrop4: false,
				professionalList:[
					{
						professionalName:'护师',
						professionalGetTime:'2012-05-01',
						professionalJob:'护师',
						professionalTime:'2015-07-30',
						Age:'5'
					},
					{
						professionalName:'护师',
						professionalGetTime:'2012-05-01',
						professionalJob:'护师',
						professionalTime:'2015-07-30',
						Age:'5'
					},
				],
				PositionList: [{
						PositionName: '呼吸内副护士长',
						PositionJob: '副护士长',
						PositionTime: '2015-06-01'
					},
					{
						PositionName: '呼吸内副护士长',
						PositionJob: '副护士长',
						PositionTime: '2015-06-01'
					},
					{
						PositionName: '呼吸内副护士长',
						PositionJob: '副护士长',
						PositionTime: '2015-06-01'
					},
				],
				userinfo: {},
				severList: [{
						name: '基本信息',
						icon: 'point.png'
					},
					{
						name: '职称变动',
						icon: 'quan.png'
					},
					{
						name: '职务变动',
						icon: 'momey.png'
					},
					{
						name: '教育经历',
						icon: 'renw.png'
					},
					{
						name: '工作经历',
						icon: 'bank.png'
					},
				],
			}
		},
		computed: {
			computedIfName() {
				return li_i => {
					if (this[`iname${li_i}`]) {
						return true
					} else
						return false
				};
			}
		},
		onLoad() {
			//加载
			this.init();
		},
		onShow() {
			// 页面加载时执行的代码
			// 在mounted钩子中，动态地为每个元素生成一个唯一的v-if变量名
			this.severList.forEach((li, li_i) => {
				const ifName = `iname${li_i}`;
				this[ifName] = li_i % 2 ? true : false;
			});
		},
		methods: {
			init() {
				//用户信息
				this.userinfo = {
					face: '../../static/HM-PersonalCenter/face.jpeg',
					username: "VIP会员10240",
					integral: "1435"
				}
			},
			//用户点击列表项
			dropdown(li_i) {
				if (li_i === 0) {
					this.showdrop0 = !this.showdrop0
				} else if (li_i === 1) {
					this.showdrop1 = !this.showdrop1
				} else if (li_i === 2) {
					this.showdrop2 = !this.showdrop2
				} else if (li_i === 3) {
					this.showdrop3 = !this.showdrop3
				} else if (li_i === 4) {
					this.showdrop4 = !this.showdrop4
				}
			}

		}
	}
</script>

<style lang="scss">
	page {
		background-color: #fff
	}

	table {
		border-collapse: collapse;
		margin: 5upx;
	}

	th,
	td {
		border: 1px solid #ccc;
		 vertical-align: middle; /* 或者是 middle */
	}

	.table-row {
		display: inline-block;
		width: 33%;
	}
	.table-row2{
		display: inline-block;
		width: 25%;
	}

	.line {
		height: 1upx;
		background: #ddd;
		width: 100%;
		margin-bottom: 3upx;
	}

	.header {
		&.status {
			padding-top: var(--status-bar-height);
		}

		background-color:#ff6364;
		width:100%;
		height:30vw;
		padding:0 4%;
		display:flex;
		align-items:center;

		.userinfo {
			width: 90%;
			display: flex;

			.face {
				flex-shrink: 0;
				width: 15vw;
				height: 15vw;

				image {
					width: 100%;
					height: 100%;
					border-radius: 100%
				}
			}
		}

		.setting {
			flex-shrink: 0;
			width: 6vw;
			height: 6vw;

			image {
				width: 100%;
				height: 100%
			}
		}
	}

	.hover {
		background-color: #eee
	}

	.list {
		width: 100%;
		margin: auto;
		border-bottom: solid 26upx #f1f1f1;

		.info {
			width: 100%;
			// height: 120upx;
			text-align: justify;

			text {
				text-align: justify;
				margin-left: 20upx;
				margin-top: 8upx;
			}
		}

		.li {
			width: 96%;
			// height: 100upx;
			padding-left: 8%;
			border-bottom: solid 1upx #e7e7e7;
			display: flex;
			flex-wrap: wrap;
			align-items: center;

			&.noborder {
				border-bottom: 0
			}


			.label {
				width: 100%;
				height: 100upx;
				display: flex;
				align-items: center;
				justify-content: center;

				.icon {
					flex-shrink: 0;
					width: 50upx;
					height: 50upx;

					image {
						width: 50upx;
						height: 50upx
					}
				}

				.text {
					padding-left: 20upx;
					width: 100%;
					color: #666
				}

				.to {
					flex-shrink: 0;
					width: 40upx;
					height: 40upx;
					margin-right: 1%;
				}
			}
		}
	}
</style>