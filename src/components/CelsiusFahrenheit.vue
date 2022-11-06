<template>
	<section class="converter">
		<input class="converter__input" type="number" placeholder="C" v-model="valueCelsius"/>
		<div class="converter__output">{{ valueFahrenheit }}F</div>
	</section>
</template>

<script>
	export default{
		data() {
			return {
				valueCelsius: 10,
			}
		},

		computed: {
			valueFahrenheit() {
				return(this.valueCelsius * 1.8) + 32;
			}
		},
	}
</script>

<style>
	.converter {
		display: flex;
	}

	.converter__input {
		background: inherit;
		border: 1px solid white;
	}
</style>