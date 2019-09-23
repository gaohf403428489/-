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
				<span style="top: -4rem;position: relative;font-size: 2.2rem;color: red;">账户注册</span><br/>
				<label for="username">输入昵称</label>
				<input style="height:40px;" size="28" type="text" placeholder="请输入您的昵称" id="username" v-model="username" /><br>
				<br/><label for="phonenum">输入账号</label>
				<!--  v-model="username":监听username的变化 -->
				<input style="height:40px;" size="28" type="text" placeholder="请输入您注册时的手机号" id="phonenum" v-model="phonenum" /><br>
				<br/><label for="password">输入密码</label>
				<input style="height:40px;" size="28" type="password" placeholder="请输入您的密码" id="password" v-model="password" />
				<br>
				<br/><label for="passwordagain">确认密码</label>
				<input style="height:40px;" size="28" type="password" placeholder="请再次输入您的密码" id="passwordagain" v-model="passwordagain" />
				<br>
				<br/><button v-on:click="register" type="button" style="width:30rem; background: red;border-radius: 7px;">立即注册</button>
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
		name: 'register',
	  data () {
	    return {
		  username:"",
	      phonenum:"",
		  password:"",
		  passwordagain:""
	    }
	  },
		methods: {
			register: function() {
				let that = this;
				that.$http.post("http://127.0.0.1:5000/user/register/", {
					username:that.username,
					phonenum: that.phonenum,
					password: that.password,
					passwordagain:that.passwordagain
				}).then(function(response) {
					if (parseInt(response.data.code) === 200) {
						//注册成功，跳转到登录界面
						 that.$router.push('login')
					}
				}).catch(function(error) {
					console.log("错了")
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
