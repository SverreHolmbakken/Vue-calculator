<template>
	<section class="hamburger-component">
		<button @click="toggleCollapse" class="hamburger-component__button">
			
			<svg class="hamburger-icon" width="88" height="54" viewBox="0 0 88 54" fill="none" xmlns="http://www.w3.org/2000/svg">
				<rect width="88" height="10" rx="5" fill="#D9D9D9"/>
				<rect y="22" width="88" height="10" rx="5" fill="#D9D9D9"/>
				<rect y="44" width="88" height="10" rx="5" fill="#D9D9D9"/>
			</svg>
		</button>
		
		<span class="">{{ title }}</span>

		<div v-if="isCollapsed === false" class="hamburger-component__content">
			<slot/>
		</div>
	</section>
</template>

<script>
	export default {
		props: {
			title: {
				type: String
			}
		},
		
		data() {
			return {
				isCollapsed: true
			}
		},

		methods: {
			toggleCollapse() {
				this.isCollapsed = !this.isCollapsed;
			}
		}
	}
</script>

<style>
	.hamburger-component {
		margin: 10px;
	}

	.hamburger-component__content {
		position: absolute;
		height: 100%;
		width: 18rem;
		top: 0;
		left: 8.45rem;
		z-index: 5;
		box-shadow: 4px 0px 4px rgba(0, 0, 0, 0.25);
		background: white;
	}
	
	.hamburger-component__button {
		width: fit-content;
		cursor: pointer;
		border: 0;
		margin: 0;
		display: flex;
		justify-content: space-between;
		z-index: 20;
	}

	.hamburger-icon:hover {
		fill: #DA4567;
	}

	.hamburger-component__content,
	.hamburger-component__button {
		padding: 10px;
	}
</style>