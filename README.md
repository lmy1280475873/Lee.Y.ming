<!DOCTYPE html>
<html>

	<head>
		<meta charset="UTF-8">
		<title></title>
		<style type="text/css">
			* {
				margin: 0;
				padding: 0;
			}
			
			ul {
				list-style: none;
				width: 300px;
				margin: 30px auto;
				background-color: #F0FFFF;
			}
			
			ul li {
				padding: 10px;
				padding-right: 60px;
				text-align: right;
				height: 40px;
			}
			
			#level {
				margin-left: 50px;
				width: 200px;
			}
			
			#level span {
				display: inline-block;
				width: 50px;
				height: 20px;
				border: 1px solid #A9A9A9;
				margin: 5px;
				background-color: ghostwhite;
				text-align: center;
				line-height: 20px;
			}
		</style>
	</head>

	<body>
		<ul>
			<li>
				用户名:<input type="text" name="" id="" placeholder="用户登录名" />
			</li>
			<li>
				密码:<input type="password" name="" id="pwd" placeholder="6-10位数字和字母组成" />
			</li>
			<li>
				确认密码:<input type="password" name="" id="rePwd" placeholder="6-10位数字和字母组成" />
			</li>
			<div id="level">
				<span>弱</span>
				<span>中</span>
				<span>强</span>
			</div>
			<li><input type="button" value="注册" id="btn" /></li>
		</ul>

		<script type="text/javascript">
			var pwd = document.getElementById("pwd");
			var level = document.getElementById("level");
			var rePwd = document.getElementById("rePwd");
			var span = level.getElementsByTagName('span');

			pwd.onchange = function() {
					var pass = pwd.value;
					pwdLevel(pass);
				}
				// 封装函数 判断密码强度
			function pwdLevel(pwd) {
				console.log(pwd);
				// 判断密码是否满足规则
				var reg = /^[\d|a-z|A-Z]{6,10}$/;
				if(reg.test(pwd)) {
					console.log('密码满足')
				} else {
					console.log('密码不符合规则')
					span[0].style.backgroundColor = 'ghostwhite';
					span[1].style.backgroundColor = 'ghostwhite';
					span[2].style.backgroundColor = 'ghostwhite';
					return null;
				}
				// 判断等级
				// 低: 纯数字或者纯字母
				// 中: 数字和小写字母或大写字母混合
				// 强: 数字和大小写字母混合
				var lv1 = /\d+/ // 包含数字
				var lv2 = /[a-z]+/; // 包含小写字母
				var lv3 = /[A-Z]+/; // 包含大写字母

				if(lv1.test(pwd) || lv2.test(pwd) || lv3.test(pwd)) {
					span[0].style.backgroundColor = '#FF7F50';
					span[1].style.backgroundColor = 'ghostwhite';
					span[2].style.backgroundColor = 'ghostwhite';
				}
				if(lv1.test(pwd) && lv2.test(pwd) || lv1.test(pwd) && lv3.test(pwd) || lv2.test(pwd) && lv3.test(pwd)) {
					span[0].style.backgroundColor = 'yellow';
					span[1].style.backgroundColor = 'yellow';
					span[2].style.backgroundColor = 'ghostwhite';
				}
				if(lv1.test(pwd) && lv2.test(pwd) && lv3.test(pwd)) {
					span[0].style.backgroundColor = '#1E90FF';
					span[1].style.backgroundColor = '#1E90FF';
					span[2].style.backgroundColor = '#1E90FF';
				}
			}
			rePwd.onchange = function() {
				if(rePwd.value != pwd.value) {
					rePwd.value = '';
					alert('两次密码输入不一致')
				}
			}
		</script>
	</body>

</html>
