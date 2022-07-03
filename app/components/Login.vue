<template>
	<Page ref="page" :actionBarHidden="true" :backgroundSpanUnderStatusBar="true">
		<StackLayout class="login" >
			<Image src="~/assets/login/login.png"></Image>
			<FlexboxLayout class="tabbar" alignItems="center" justifyContent="center">
				<Label :class="['tab-item',type!='email'?'active':'']" @tap="change('account')" text="账号登录" />
				<Label :class="['tab-item',type=='email'?'active':'']" @tap="change('email')" text="电子邮箱登录" />
			</FlexboxLayout>
			<FlexboxLayout class="line" alignItems="center" :justifyContent="type!='email'?'flex-start':'flex-end'">
				<label class="line-item" />
			</FlexboxLayout>
			<FlexboxLayout v-if="type!='email'" class="form" flexDirection="column" alignItems="center"
				justifyContent="center">
				<FlexboxLayout class="input" alignItems="center">
					<Image class="icon" src="~/assets/login/zh.png" stretch="aspectFill" />
					<TextField class="TextField" v-model="form.username" hint="请输入账号" />
				</FlexboxLayout>
				<FlexboxLayout class="input" alignItems="center">
					<Image class="icon" src="~/assets/login/lock1.png" stretch="aspectFill" />
					<TextField :secure="true" color="#999999" class="TextField" v-model="form.password" hint="请输入密码" />
				</FlexboxLayout>
			</FlexboxLayout>
			<FlexboxLayout v-else class="form" flexDirection="column" alignItems="center" justifyContent="center">
				<FlexboxLayout class="input" alignItems="center">
					<Image class="icon" src="~/assets/login/email.png" stretch="aspectFill" />
					<TextField keyboardType="email" class="TextField" v-model="form.username" hint="请输入电子邮箱" />
				</FlexboxLayout>
				<FlexboxLayout class="input" alignItems="center">
					<Image class="icon" src="~/assets/login/lock1.png" stretch="aspectFill" />
					<TextField lineHeight="90" keyboardType="number" maxLength="6" :secure="true" color="#999999"
						class="TextField" v-model="form.password" hint="请输入验证码" />
					<Button class="codeBtn"  @tap="blur" text="发送验证码" tap="onTap" />
				</FlexboxLayout>
			</FlexboxLayout>
			<FlexboxLayout class="tips" alignItems="center" justifyContent="space-between">
				<Label @tap="goPage" class="tips-text">注册账号</Label>
				<Label class="tips-text">忘记密码？</Label>
			</FlexboxLayout>
			<Button class="submit" text="登录" tap="onTap" />
		</StackLayout>
	</Page>
</template>

<script lang="ts">
	import {
		Vue,
		Component
	} from "vue-property-decorator";
	import reg from "./reg.vue";
	interface form {
		username: string;
		password: string;
	}
	@Component({})
	export default class Login extends Vue {
		type: string = "emile"
		form: form = {
			username: "",
			password: ""
		}
		change(e: string) {
			this.type = e;
		}

		goPage() {
			this.$navigateTo(reg);
		}
		blur(args:any) {
			console.log(123456789);
			const myTextField = args.object;
			myTextField.dismissSoftInput();
		}
	}
</script>

<style lang="scss">
	$color:#8381ff;

	.login {
		.tabbar {
			width: 70%;
			margin-top: 150px;

			.tab-item {
				height: 80px;
				line-height: 80px;
				width: 50%;
				text-align: center;
				display: inline-block;
				font-weight: bold;
				font-size: 18px;
				color: #c7c7c7;
			}

			.active {
				color: $color;
			}
		}

		.line {
			width: 70%;
			height: 4px;
			background-color: #c7c7c7;

			.line-item {
				width: 50%;
				height: 4px;
				background-color: $color;
			}
		}

		.tips {
			width: 70%;
			margin-top: 40px;

			.tips-text {
				font-size: 17px;
				color: $color;

				&:active {
					color: #c7c7c7;
				}
			}
		}

		.form {
			margin-top: 100px;
			width: 80%;

			.input {
				height: 100px;
				border-bottom-width: 1px;
				border-color: #eaeaea;
				width: 90%;
				padding: 5px 15px;
				margin-top: 40px;

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
			margin-top: 100px;

			&:active {
				transform: scale(0.95);
			}
		}
	}
</style>
