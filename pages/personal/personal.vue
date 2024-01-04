<template>
	<view class="body">
		<view class="top-box">
			<view class="row-box" v-if="1" @click="toBaseInfo()">
				<image class="avatar" src="../../static/avatar/avatar.png"></image>
				   <view class="username">用户名</view>
			</view>
			
				
			
			<!-- <view class="row-box" v-else @click="turnLogin()">
				
				<view class="no-login-text-box">
					<text class="login">点击注册/登录</text>
					<text class="welcome">欢迎来到护理系统</text>
				</view>
			</view> -->
		</view>
	</view>
	
	
</template>

<script>
</script>

<style >
	body{
		display: flex;
		/* width: 100px; */
	}
	  .avatar {
	    width: 120rpx;
	    height: 120rpx;
	    border-radius: 50%;
		float: left;
	  }
	  .username {
		float: left;
	    margin-top: 10px;
	    font-size: 36rpx
	  }
	  .top-box{
		  width: 100%;
		  background: gray;
	  }
</style>