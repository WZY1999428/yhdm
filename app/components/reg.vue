<template>
	<Page>
		<ActionBar title="注册" :flat="true">
			<NavigationButton android.systemIcon="ic_menu_back" />
		</ActionBar>
		<StackLayout class="reg">
			<FlexboxLayout class="title">
				<label text="注册" />
			</FlexboxLayout>
			<FlexboxLayout class="form" flexDirection="column" alignItems="center" justifyContent="center">
				<FlexboxLayout class="input" alignItems="center">
					<Image class="icon" src="~/assets/login/zh.png" stretch="aspectFill" />
					<TextField class="TextField" v-model="form.username" hint="请输入账号" />
				</FlexboxLayout>
				<FlexboxLayout class="input" alignItems="center">
					<Image class="icon" src="~/assets/login/lock1.png" stretch="aspectFill" />
					<TextField :secure="true" color="#999999" class="TextField" v-model="form.password" hint="请输入密码" />
				</FlexboxLayout>
				<FlexboxLayout class="input" alignItems="center">
					<Image class="icon" src="~/assets/login/email.png" stretch="aspectFill" />
					<TextField keyboardType="email" class="TextField" v-model="form.email" hint="请输入电子邮箱" />
				</FlexboxLayout>
				<FlexboxLayout class="input" alignItems="center">
					<Image class="icon" src="~/assets/login/lock1.png" stretch="aspectFill" />
					<TextField lineHeight="90" keyboardType="number" maxLength="6" :secure="true" color="#999999"
						class="TextField" v-model="form.code" hint="请输入验证码" />
					<Button class="codeBtn" text="发送验证码" tap="onTap" />
				</FlexboxLayout>
			</FlexboxLayout>
			<Button class="submit" text="注册" tap="onTap" />
		</StackLayout>
	</Page>
</template>

<script lang="ts">
	import {
		Vue,
		Component
	} from "vue-property-decorator";
	interface form {
		username: string;
		password: string;
		email: string;
		code: string|number;
	}

	@Component({})
	export default class Login extends Vue {
		form: form = {
			username: "",
			password: "",
			email:"",
			code:"",
		}
	}
</script>

<style lang="scss">
	$color:#8381ff;

	.reg {
		.title {
			margin-top: 40px;
			height: 180px;
			padding: 20px 50px;
			font-weight: bold;

			Label {
				color: #666;
				font-size: 35px;
			}
		}

		.form {
			width: 80%;
			.input {
				height: 100px;
				border-bottom-width: 1px;
				border-color: #eaeaea;
				width: 90%;
				padding: 5px 15px;
				margin-top: 80px;

				.icon {
					width: 35px;
					height: 30px;
				}

				.TextField {
					flex: 1;
					border-bottom-width: 0;
					height: 80px;
					font-size: 18px;
				}

				.codeBtn {
					color: #fff;
					width: 180px;
					height: 60px;
					background-color: $color;
					border-radius: 80px;
				}
			}
		}

		.submit {
			width: 70%;
			background-color: $color;
			color: #fff;
			font-weight: bold;
			font-size: 20px;
			border-radius: 80px;
			margin-top: 250px;

			&:active {
				transform: scale(0.95);
			}
		}
	}
</style>
