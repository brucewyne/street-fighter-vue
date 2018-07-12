<template>
	<div id="app">
		<h1>Street Fighter</h1>
		<div class="fighters row">
			<div class="player figher column">
				<span class="fighter-name">Player 1</span>
				{{playerHealth}}
			</div>
			<div class="opponent fighter column">
				<span class="fighter-name">Opponent</span>
				{{opponentHealth}}
			</div>
		</div>
		<div class="row">
			<div class="column">
				<custom-button :button-style="'green'" @pressed="handleAttackButton"></custom-button>
				<custom-button :button-style="'red'" @pressed="handleSpecialAttackButton"></custom-button>
			</div>
			<div class="column">
				<log :messages="messageLog"></log>
			</div>
		</div>
		<!-- modal -->
			<!-- Game over text -->
			<!-- Button (plain) -->
		<!--/ modal -->
	</div>
</template>

<script>

import CustomButton from './components/Button';
import Log from './components/Log';

export default {
	data() {
		return {
			playerHealth: 100,
			opponentHealth: 100,
			messageLog: [],
			showModal: false,
			gameInPlay: true,
			gameOverMessage: ""
		}
	},
	methods: {
		getRandomDamageAmount: function(min, max) {
			return Math.floor(Math.random() * (max - min + 1)) + min;
		},
		handleAttackButton: function(){
			let damage = this.getRandomDamageAmount(5,9);
			this.opponentHealth = this.opponentHealth - damage;
			this.messageLog.push(`Player used Attack and did ${damage} damage.`);
		},
		handleSpecialAttackButton: function(){
			let damage = this.getRandomDamageAmount(8,12);
			this.opponentHealth = this.opponentHealth - damage;
			this.messageLog.push(`Player used Attack and did ${damage} damage.`);
		}
	},
	components: {
		CustomButton,
		Log
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
