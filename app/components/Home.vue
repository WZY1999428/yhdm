<template>
	<Page>
		<ActionBar>
			<Label text="Home" />
		</ActionBar>

		<GridLayout>
			<Label :text="name"></Label>
		</GridLayout>
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
       name:string="123456789"
	}
</script>

<style scoped lang="scss">
	@import '@nativescript/theme/scss/variables/blue';

	// Custom styles
	.fas {
		@include colorize($color: accent);
	}

	.info {
		font-size: 20;
		horizontal-align: center;
		vertical-align: center;
	}
</style>
