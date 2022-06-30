<template>
	<Page ref="page" :actionBarHidden="true" :backgroundSpanUnderStatusBar="true">
		<StackLayout class="login">
			<Image src="~/assets/login/login.png"></Image>
			<FlexboxLayout class="form" alignItems="center" justifyContent="center">
				<Label class="tabbar" @tap="change('0%')" text="账号登录" />
				<Label class="tabbar" @tap="change('200%')" text="电子邮箱登录" />
			</FlexboxLayout>
			<AbsoluteLayout class="line" alignItems="center" justifyContent="center">
				<label :left="left" class="line-item" />
			</AbsoluteLayout>
		</StackLayout>
	</Page>
</template>

<script lang="ts">
	import {
		Vue,
		Component
	} from "vue-property-decorator";
	@Component({
	})
	export default class Login extends Vue {
		left: string = "0%";
		change(e: string): void {
			this.left = e
		}
	}
</script>

<style lang="scss">
	.login {
		.form {
			width: 50%;
			margin-top: 150px;

			.tabbar {
				width: 50%;
				text-align: center;
				display: inline-block;
				font-weight: bold;
				color: #8381ff;
				font-size: 18px;
				margin-bottom: 20px;
			}
		}

		.line {
			width: 50%;
			height: 4px;
			background-color: #c7c7c7;

			.line-item {
				width: 50%;
				height: 4px;
				transition: all 0.5s;
				background-color: #8381ff;
			}
		}
	}
</style>
