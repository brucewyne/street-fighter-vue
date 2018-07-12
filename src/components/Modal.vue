<template>
	<div v-if="visible" class="overlay" @click="closeOverlay">
		<div class="modal">
			<span class="modal-close" @click="closeOverlay">
				&times;
			</span>	
			<div class="modal-content">
				<slot></slot>
			</div>
		</div>	
	</div>	
</template>

<script>
	export default {
		props: ['visible'],
		methods: {
			closeOverlay: function() {
				this.visible = false;
			}
		}
	}
</script>

<style lang="scss">
.overlay {
	background: rgba(190, 0, 0, 0.6);
	left: 0;
	height: 100%;
	position: fixed;
	top: 0;
	width: 100%;
	.modal {
		background: white;
		box-shadow: 0 0 10px darkred;
		left: 50%;
		max-width: 600px;
		margin: 0 auto;
		min-height: 100px;
		padding: 40px;
		position: fixed;
		top: 50%;
		transform: translate(-50%,-50%);
		.modal-close {
			font-size: 24px;
			position: absolute;
			right: 10px;
			top: 10px;
		}
	}
}
</style>