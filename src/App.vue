<template>
	<div id="app">
		<h1>Street Fighter</h1>
		<div class="fighters row">
			<div class="player figher column">
				<span class="fighter-name">Player 1</span>
				<health-meter :health-value="playerHealth"></health-meter>
			</div>
			<div class="opponent fighter column">
				<span class="fighter-name">Player 1</span>
				<health-meter :health-value="opponentHealth"></health-meter>
			</div>  
		</div>
		<div class="row">
			<div class="column">
				<custom-button v-if="gameInPlay" :button-style="'green'" @pressed="handlePunchButton"></custom-button>
				<custom-button v-if="gameInPlay" :button-style="'red'" @pressed="handleSpecialButton"></custom-button>
			</div>  
			<div class="column">
				<log :messages="messageLog"></log>
			</div>  
		</div>
		<modal :visible="showModal">
			<div v-html="gameOverMessage"></div>
			<custom-button :button-style="'plain'" @pressed="handleResetButton">
				Challenge Accepted
			</custom-button>
		</modal>
	</div>
</template>

<script>
import CustomButton from './components/Button';
import Log from './components/Log';
import HealthMeter from './components/HealthMeter';
import Modal from './components/Modal';

export default {
  name: 'App',
  data() {
		return {
			playerHealth: 100,
			opponentHealth: 100,
			messageLog: [],
			showModal: false,
			gameInPlay: true,
			gameOverMessage: ''
		}
	},
	components: {
			CustomButton,
			HealthMeter,
			Log,
			Modal
		},
	methods: {
		getRandomDamageAmount: function(min, max) {
			return Math.floor(Math.random() * (max - min + 1)) + min;
		},
		handleSpecialButton: function() {
			let damage = this.getRandomDamageAmount(8,12);
			this.opponentHealth = this.opponentHealth - damage;
			this.messageLog.push(`Player used Special Attack and did ${damage} damage`);
			this.checkForGameOver();
			this.opponentsTurn();
		},
		handlePunchButton: function() {
			let damage = this.getRandomDamageAmount(5,9);
			this.opponentHealth = this.opponentHealth - damage;
			this.messageLog.push(`Player used Special Attack and did ${damage} damage`);
			this.checkForGameOver();
			this.opponentsTurn();
		},
		handleResetButton: function() {
			this.reset();
		},
		opponentsTurn: function() {
			if (this.gameInPlay) {
				let damage = this.getRandomDamageAmount(5,15);
				this.playerHealth = this.playerHealth - damage;
				this.messageLog.push(`Opponent attacks and does ${damage} damage`);
				this.checkForGameOver();
			}
		},
		checkForGameOver: function() {
			if (this.opponentHealth <= 0 || this.playerHealth <= 0) {
				this.gameInPlay = false;
				this.showModal = true;
				if (this.opponentHealth <= 0) {
					this.messageLog.push('Player won!');
					this.gameOverMessage = "<p>Player won. Play again?</p>"
				}
				if (this.playerHealth <= 0) {
					this.messageLog.push('Man, you suck!');
					this.gameOverMessage = "<p>You lose. Play again?</p>"
				}
			}
		},
		reset: function() {
			this.opponentHealth = 100;
			this.playerHealth = 100;
			this.messageLog = [];
			this.showModal = false;
			this.gameInPlay = true;
		}
	}
}
</script>

<style lang="scss">
#app {
	font-family: Arial, Helvetica, sans-serif
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
