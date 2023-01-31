<template>
	<section class="collapsible-component">
		<button @click="toggleCollapse" class="collapsible-component__button">
			<span>{{ title }}</span>
			<span>++++</span>
		</button>

		<div v-if="isCollapsed === false" class="collapsible-component__content">
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
	.collapsible-component {
		border: 2px solid yellow;
		margin: 10px;
	}

	.collapsible-component__button {
		width: 100%;
		cursor: pointer;
		border: 0;
		margin: 0;
		display: flex;
		justify-content: space-between;
		border-bottom: 2px solid yellow;
	}

	.collapsible-component__button:hover {
		background: yellow;
		color: black;
	}

	.collapsible-component__content,
	.collapsible-component__button {
		padding: 10px;
	}
</style>