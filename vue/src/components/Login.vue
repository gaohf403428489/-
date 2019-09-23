<template>

	<div id="login">
		<!-- 顶部导航栏 -->
		<div id="header">
			<span style="left: 250px;position: absolute;top: 2rem;"><img src="../../static/img/1.png"></span>
			<span style="left: 350px;position: absolute;top: 3rem;color: white;font-size:3rem;">BIANJI</span>
			<span style="left: 115rem;position: absolute;top: 3rem;color: white;font-size:3rem;">welcome to BIANJI.store</span>
		</div>
		<!--  -->
		<div style="background-image: url(../static/img/2.jpg);width: 100%;height: 50rem;background-repeat: no-repeat; position: relative;top: 9rem;">
			<div style="background-color: white;width: 54.6rem;height: 47.6rem;float: right;">
				<footer>
					<router-link class="login" active-class="loginActive" to='/login'><dl><dd>点击登录</dd></dl></router-link>
					<router-link class="register" active-class="registerActive" to='/register'><dl><dd>点击注册</dd></dl></router-link>
				</footer>
			</div>
		</div>
		<div class="loginPagr">
			<form>
				<span style="top: -6rem;position: relative;font-size: 2.2rem;color: red;">账户登录</span><br />
				<label for="phonenum">账号</label>
				<!--  v-model="username":监听username的变化 -->
				<input style="height:40px;" size="28" type="text" placeholder="请输入您注册时的手机号" id="phonenum" v-model="phonenum" /><br>
				<br /><label for="password">密码</label>
				<input style="height:40px;" size="28" type="password" placeholder="请输入您的密码" id="password" v-model="password" />
				<br>
				<br /><button v-on:click="login" type="button" style="width:24rem; background: red;border-radius: 7px;position: relative; left: 3.2rem;">立即登录</button>
			</form>
		</div>
		<div id="lowest" style="height: 100px;top: 8rem; position: relative;text-align: center;">
			<span>关于我们</span>
			<span>|</span>
			<span>联系我们</span>
			<span>|</span>
			<span>人才招聘</span>
			<span>|</span>
			<span>商家入驻</span>
			<span>|</span>
			<span>广告服务</span>
			<span>|</span>
			<span>BIANJI</span>

		</div>
		<div style="position: relative;top: 9rem; text-align: center;">
			<span style="font-size: 2rem;color: red;">版权所属:项目组第五组</span>
		</div>

	</div>
</template>

<script>
	/*js*/
	export default {
		name: 'login',
		data() {
			return {
				phonenum: "",
				password: ""
			}
		},
		methods: {
			login: function() {
				let that = this;
				that.$http.post("http://127.0.0.1:5000/user/login/", {
					phonenum: that.phonenum,
					password: that.password
				}).then(function(response) {
					if (parseInt(response.data.code) === 400) {
						// 登录失败  
						that.phonenum = '';
						that.password = '';
					} else if (parseInt(response.data.code) === 200) {
						alert("登录成功")
						that.$router.push('mainpage')
						
					}
				}).catch(function(error) {
					console.log("88888")
				})
			}
		}
	}
</script>
<style scoped>
	#login form {
		position: absolute;
		top: 15em;
		left: 118rem;

	}

	#header {
		position: absolute;
		top: 0;
		width: 100%;
		height: 9rem;
		background: black;
	}
footer a{
	display: block;
	text-align: center;
	flex: 1;
	border: #007AFF;
	
}
footer{
	border: #000000;
	position: absolute;
	top: 50rem;
	display: flex;
}
footer a{
	display: block;
	text-align: center;
	flex: 1;
	border: #007AFF;
	top: -7rem;
	
}
footer .register{
	position: relative;
	width: 150px;
	left: 30rem;
	font-size: 10px;
	border-radius: 5px;
	background: red;
	font-size: 20px;
	text-decoration: none;
}
footer .login{
	position: relative;
	left: 10rem;
	font-size: 20px;
	border-radius: 5px;
	background: red;
	text-decoration: none;
}
#lowest span{
	padding: 20px;
}
</style>
