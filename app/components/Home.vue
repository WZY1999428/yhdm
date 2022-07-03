<template>
	<Page :actionBarHidden="true" :backgroundSpanUnderStatusBar="true">
		<StackLayout backgroundColor="#eaeaea">
			<FlexboxLayout class="ActionBar" alignItems="center" >
				<Image class="icon" src="~/assets/home/search.png" />
				<Label class="text">搜索</Label>
			</FlexboxLayout>
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
	export default class Home extends Vue {
		name: string = "123456789"
	}
</script>

<style scoped lang="scss">
	.ActionBar {
		width: 95%;
		height: 100px;
		padding: 0 20px;
		background-color: #d1d1d1;
		border-radius:80px;
		padding: 0 20px;
		.icon {
			width: 40px;
			height: 40px;
			margin: 0 20px;
		}
		.text{
			height: 90px;
		}
	}
</style>
