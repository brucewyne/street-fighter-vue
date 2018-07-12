<template>
	<button class="button" :class="buttonStyle" @click="handleClick">
		
	</button>	
</template>

<script>

export default {
	props: ['button-style'],
	data() {
		return {
			
		}
	},
	methods: {
		handleClick: function(){
			this.$emit("pressed");
		}
	}
}

</script>

<style lang="scss">
.button {
  cursor: pointer;
  outline: none;
  &.red {
    border: 5px solid red;
    border-radius: 50%;
    background: linear-gradient(to bottom right, darkred, red);
    height: 80px;
    width: 80px;
  }
  &.green {
    border: 5px solid green;
    border-radius: 50%;
    background: linear-gradient(to bottom right, darkgreen, green);
    height: 80px;
    width: 80px;
  }
  &.gold {
    border: 5px solid gold;
    border-radius: 50%;
    background: linear-gradient(to bottom right, goldenrod, gold);
    height: 80px;
    width: 80px;
  }
  &.plain {
    background: #ccc;
    padding: 10px 20px;
    text-align: center;
  }
}
</style>