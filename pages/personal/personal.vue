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

		<view class="list" v-for="(list,list_i) in severList" :key="list_i">
			<view class="li" ref="itemRefs" v-for="(li,li_i) in list" @tap="dropdown(list_i,li_i)"
				v-bind:class="{'noborder':li_i==list.length-1}" hover-class="hover" :key="li.name">
				<view class="label">
					<view class="icon">
						<image :src="'../../static/HM-PersonalCenter/sever/'+li.icon"></image>
					</view>
					<view class="text">{{li.name}}</view>
					<image class="to" src="../../static/HM-PersonalCenter/drop.png"></image>

				</view>
				<view class="line">

				</view>
				<view v-if="showDropdown" class="info bg-blue">

				</view>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				showDropdown: false,
				iconList: [{
					icon: 'moneybagfill',
					color: 'blue',
					badge: 0,
					name: '待接单'
				}, {
					icon: 'presentfill',
					color: 'red',
					badge: 0,
					name: '待上门',
					bindtap: "bindZan"
				}, {
					icon: 'formfill',
					color: 'purple',
					badge: 11,
					name: '待评价',
					bindtap: "showResource"
				}, {
					icon: 'shopfill',
					color: 'green',
					badge: 0,
					name: '返修/售后',
					bindtap: "bindPoint"
				}],
				iconOtherList: [{
					icon: 'location',
					color: 'blue',
					badge: 0,
					name: '地址管理'
				}, {
					icon: 'service',
					color: 'blue',
					badge: 0,
					name: '电话客服',
					bindtap: "bindZan"
				}, {
					icon: 'mark',
					color: 'blue',
					badge: 0,
					name: '在线客服',
					bindtap: "showResource"
				}, {
					icon: 'mail',
					color: 'blue',
					badge: 0,
					name: '投诉',
					bindtap: "bindCollect"
				}, {
					icon: 'settings',
					color: 'blue',
					badge: 0,
					name: '设置',
					bindtap: "bindZan"
				}],
				//#ifdef APP-PLUS
				isH5Plus: true,
				//#endif
				//#ifndef APP-PLUS
				isH5Plus: false,
				//#endif
				userinfo: {},
				orderTypeLise: [
					//name-标题 icon-图标 badge-角标
					{
						name: '待付款',
						icon: 'l1.png',
						badge: 1
					},
					{
						name: '待发货',
						icon: 'l2.png',
						badge: 2
					},
					{
						name: '待收货',
						icon: 'l3.png',
						badge: 6
					},
					{
						name: '待评价',
						icon: 'l4.png',
						badge: 9
					},
					{
						name: '退换货',
						icon: 'l5.png',
						badge: 0
					}
				],
				severList: [
					[{
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
				],
			}
		},
		onLoad() {
			//加载
			this.init();
		},
		onReady() {
			dropdown(list_i, li_i) {
				// // if(li_i === 0){
				// 在DOM渲染完成后，引用已经被正确绑定了
				console.log(this.$refs.itemRefs);
				// // }
			};
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
			//用户点击订单类型
			toOrderType(index) {
				uni.showToast({
					title: this.orderTypeLise[index].name
				});
			},
			//用户点击列表项
				dropdown(list_i, li_i) {
					// // if(li_i === 0){
					// 在DOM渲染完成后，引用已经被正确绑定了
					console.log(this.$refs.itemRefs);
					// // }
				}

		}
	}
</script>

<style lang="scss">
	page {
		background-color: #fff
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
			height: 350upx;
			display: flex;

		}

		.li {
			width: 92%;
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