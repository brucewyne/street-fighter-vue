<template>
	<div class="progress-bar">
		<div style="width: " class="progress-amount"></div>
	</div>	
</template>

<script>

</script>

<style lang="scss">
	.progress-bar {
	background: #eee;
	border: 1px solid #aaa;
	height: 15px;
	.progress-amount {
		background: green;
		height: 100%;
		transition: .5s ease all;
	}
}
</style>