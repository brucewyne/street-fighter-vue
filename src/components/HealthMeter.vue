<template>
	<div class="progress-bar">
		<div :style="{width: this.progressBarWidth}" class="progress-amount"></div>
		{{this.healthValue}}
	</div>
</template>

<script>
export default {
	props: ['healthValue'],
	data() {
		return {
			
		}
	},
	computed: {
		progressBarWidth: function() {
			if (this.healthValue < 0) {
				return 0 + '%';
			}
			return this.healthValue + '%';
		}
	}
}
</script>

<style lang="scss">
.progress-bar {
	background: #eee;
	border: 1px solid #aaa;
	height: 15px;
	.progress-amount {
		background: green;
		height: 100%;
	}
}
</style>