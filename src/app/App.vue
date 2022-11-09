<template>
	<HamburgerCopy :title="''">
		<h2 class="hamburger-component__title">Konvertering</h2>
		
		<div class="hamburger-component__subtitle">
			<button @click="switchComponent('Calculator')" class="hamburger-component__subtitle-text">Kalkulator</button>
			<button @click="switchComponent('LengthCalc')" class="hamburger-component__subtitle-text">Distanse</button>
			<button @click="switchComponent('WeightCalc')" class="hamburger-component__subtitle-text">Vekt og masse</button>
			<button @click="switchComponent('TemperatureCalc')" class="hamburger-component__subtitle-text">Temperatur</button>
		</div>

		<div class="hamburger-component__title-underline"></div>
		
	</HamburgerCopy>	
	
	<Calculator v-if="selectedComponent === 'Calculator'" />
	<LengthCalc v-if="selectedComponent === 'LengthCalc'" />
	<WeightCalc v-if="selectedComponent === 'WeightCalc'" />
	<TemperatureCalc v-if="selectedComponent === 'TemperatureCalc'" />
	<!-- <HamburgerCopy/> -->
</template>

<script>

	import Calculator from '../components/Calculator.vue';
	import HamburgerCopy from '../components/HamburgerCopy.vue';
	import LengthCalc from '../components/LengthCalc.vue';
	import WeightCalc from '../components/WeightCalc.vue';
	import TemperatureCalc from '../components/TemperatureCalc.vue';
	
	export default {
		components: {
			Calculator,
			HamburgerCopy,
			LengthCalc,
			WeightCalc,
			TemperatureCalc,

		},

		data() {
			return {
				selectedComponent: 'Calculator'
			}
		},

		methods: {
			switchComponent(componentName) {
				this.selectedComponent = componentName;
			}
		}
	}
</script>

<style>
	/* @import 'style.css'; */
	html {
		font-size: 20px;
	}
	
	* {
		box-sizing: border-box;
		margin: 0;
		padding: 0;
	}

	body {
		background: white;
		color: black;
	}

	.title {
		position: fixed;
		height: 15%;
		left: 50%;
		top: 0;
		transform: translate(-50%);
		width: fit-content;
		z-index: 1;
	}

	.title__text {
		position: relative;
		text-align: center;
		top: 0;
		font-family: 'Inter';
		font-size: 4.8rem;
		font-weight: 400;;
	}

	button {
		border: none;
		font: inherit;
		background-color: inherit;
		cursor: pointer;
	}

	@media (max-width: 440px) {
		html {
			font-size: 16px;
		}
	}

	@media (max-width: 355px) {
		html {
			font-size: 12px;
		}
	}

	.hamburger-component__title {
		position: absolute;
		left: -2rem;
		display: flex;
		text-align: center;
		font-family: 'Inter';
		font-weight: 400;
		font-size: 2.25rem;
		margin: 5px 0 0 50px;
	}

	.hamburger-component__subtitle {
		position: absolute;
		width: fit-content;
		top: 7rem;
		z-index: 15;
	}

	.hamburger-component__subtitle-text {
		font-family: 'Inter';
		font-weight: 400;
		font-size: 2rem;
		margin-bottom: 1.5rem;
		text-decoration: underline;
	}

	.hamburger-component__subtitle-text:hover {
		text-decoration: none;
	}

	.hamburger-component__title-underline {
		position: fixed;
		top: 5.5rem;
		left: 0;
		background: black;
		height: 1px;
		width: 27rem;
		margin-left: -10px;
	}
</style>