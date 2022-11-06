<template>
	
	<div class="title">
		<h1 class="title__text">Kalkis</h1>
	</div>
	<Calculator/>
	<!-- <Hamburger/> -->
</template>

<script>

	import Calculator from '../components/Calculator.vue';
	// import Hamburger from '../components/Hamburger.vue';

	export default {
		components: {
			Calculator,
			// Hamburger,
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
		width: 100%;
		z-index: 10;
	}

	.title__text {
		position: relative;
		text-align: center;
		top: rem;
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
</style>