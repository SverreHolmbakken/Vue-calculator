<template>
	<section>
		<div class="hamburger-menu--closed">
			<button @click="openMenu()">
				<svg width="88" height="54" viewBox="0 0 88 54" fill="none" xmlns="http://www.w3.org/2000/svg">
					<rect width="88" height="10" rx="5" fill="#D9D9D9"/>
					<rect y="22" width="88" height="10" rx="5" fill="#D9D9D9"/>
					<rect y="44" width="88" height="10" rx="5" fill="#D9D9D9"/>
				</svg>
			</button>
		</div>

		<div class="hamburger-menu--open">
			<div class="hamburger-menu__top-box">
				<button :class="{  }" @click="closeMenu()">
						<svg width="70" height="70" viewBox="0 0 70 70" fill="none" xmlns="http://www.w3.org/2000/svg">
							<rect y="62.2254" width="88" height="10" rx="5" transform="rotate(-45 0 62.2254)" fill="#D9D9D9"/>
							<rect x="7.07108" width="88" height="10" rx="5" transform="rotate(45 7.07108 0)" fill="#D9D9D9"/>
						</svg>
				</button>

				<h2 class="hamburger-menu__title">Konvertering</h2>
			</div>

			<div class="hamburger-menu__bottom-box">
				<button class="hamburger-menu__sub-title">Normal</button>
				<button class="hamburger-menu__sub-title">Distanse</button>
				<button class="hamburger-menu__sub-title">Temperatur &deg;C -> &deg;F</button>
				<h3></h3>
			</div>
		</div>
	</section>
</template>

<script>
	export default {
		data() {
			return {
				showingMenu: false,
			}
		},

		methods: {
			openMenu() {

			},

			closeMenu() {
				this.
			}
		}
	}
</script>

<style>
	.hamburger-menu--closed {
		display: none;
		padding: .7rem;
		z-index: 15;
		
		background: lightgray;
	}

	.hamburger-menu--open {
		position: fixed;
		height: 100vh;
		width: 600px;
		z-index: 15;
		background-color: #FFF;
		box-shadow: 4px 0px 4px rgba(0, 0, 0, 0.25);
	}

	.hamburger-menu__top-box {
		display: flex;
		width: 100%;
		height: fit-content;
		padding: 0.7rem;
		padding-bottom: 0.5rem;
		border-bottom: 1px solid rgba(0, 0, 0, 0.5);
	}

	.hamburger-menu__title {
		display: flex;
		text-align: center;
		font-family: 'Inter';
		font-weight: 400;
		font-size: 2.25rem;
		margin: 5px 0 0 50px;
	}

	.hamburger-menu__bottom-box {
		position: relative;
		top: 2%;
		left: 6.5rem;
	}
	
	.hamburger-menu__sub-title {
		display: flex;
		font-family: 'Inter';
		font-weight: 400;
		font-size: 2rem;
		margin-bottom: 1.5rem;
		text-decoration: underline;
	}

	.hamburger-menu__sub-title:hover {
		text-decoration: none;
	}

	@media (max-width: 500px) {
		.hamburger-menu--open {
			width: 100vw;
		}
	}
</style>