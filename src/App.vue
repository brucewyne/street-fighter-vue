<template>
	<div id="app">
		<h1>Street Fighter</h1>
		<div class="fighters row">
			<div class="player figher column">
				<span class="fighter-name">Player 1</span>
				<!-- Health Meter -->
			</div>
			<div class="opponent fighter column">
				<span class="fighter-name">Opponent</span>
				<!-- Health Meter -->
			</div>
		</div>
		<div class="row">
			<div class="column">
				<!-- Button (green) -->
				<!-- Button (red) -->
			</div>
			<div class="column">
				<!-- message log -->
			</div>
		</div>
		<!-- modal -->
			<!-- Game over text -->
			<!-- Button (plain) -->
		<!--/ modal -->
	</div>
</template>

<script>
export default {
	data() {
		return {
			
		}
	},
	methods: {
		
	},
	components: {

	}
}
</script>

<style lang="scss">
#app {
	font-family: Arial, Helvetica, sans-serif;
}
h1 {
	font-size: 48px;
	font-weight: normal;
	margin-bottom: 30px;
	text-align: center;
}
.row {
	display: flex;
	margin: 0 auto;
	max-width: 900px;
	.column {
		flex: 1 0 50%;
		padding: 0 10px;
	}
}

.fighters {
	margin-bottom: 50px;
}
</style>
