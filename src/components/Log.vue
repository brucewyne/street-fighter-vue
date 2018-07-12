<template>
	<div class="log">
		<h2>The Log</h2>
		<ul class="message-log">
			<li v-for="(message, index) in messages" :key="index">
				{{message}}
			</li>	
		</ul>	
	</div>	
</template>

<script>
export default {
	props: ['messages']
}
</script>

<style lang="scss">
h2 {
	font-size: 18px;
	margin-bottom: 15px;
}
.message-log {
	margin: 0;
	padding: 0;
	li {
		background: #eee;
		list-style: none;
		font-size: 10px;
		margin-bottom: 5px;
		padding: 5px;
	}
}

</style>