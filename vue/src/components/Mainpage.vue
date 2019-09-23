<template>
	<div id="login">
		<h3 class="header">登录</h3>
		<div class="loginPagr">
			<form>
				<label for="phonenum">账号</label>
				<!--  v-model="username":监听username的变化 -->
				<input type="text" placeholder="please input your phonenum" id="phonenum" v-model="phonenum" /><br>
				<label for="password">密码</label>
				<input type="password" placeholder="please input your password" id="password" v-model="password" />
				<br>
				<button v-on:click="login" type="button" style="width:13rem;">点击登录</button>
			</form>
		</div>
	</div>
</template>

<script>
	/*js*/
	export default {
		name: 'login',
	  data () {
	    return {
	      phonenum:"",
		  password:""
	    }
	  },
		methods: {
			login: function() {
				let that = this;
				that.$http.post('http://127.0.0.1:5000/user/login/', {
					phonenum: that.phonenum,
					password: that.password
				}).then(function(response) {
					if (parseInt(response.data.code) === 400) {
						// 登录失败  
						that.phonenum = '';
						that.password = '';
					} else if (parseInt(response.data.code) === 200) {
							console.log("666")
					}
				}).catch(function(error) {
					console.log("88888")
				})
			}
		}
	}
</script>

<style scoped>
	#login {
		padding-bottom: 3rem;
		display: block;
	}

	#login .header {
		position: fixed;
		top: 1rem;
		text-align: center;
		width: 100%;
		background: #0F0F0F;
		line-height: 5rem;
		background: deepskyblue;
		color: white;
	}
	#login form{
		position: relative;
		top: 18rem;
	}
</style>
