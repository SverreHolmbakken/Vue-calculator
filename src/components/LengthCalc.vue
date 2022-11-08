<template>
	<div class="title">
		<h1 class="title__text">Lengdis</h1>
	</div>
	<section class="converter">
		<div class="converter__input-frame">
			<div class="converter__input">
				<div class="converter__input-text">
					{{ currentInput }} 
				</div>

				<div class="converter__input-unit">
					m
				</div>
			</div>
		</div>

		<button class="switch-icon">
			<img src="../assets/icons/switch-button.svg" alt="">
		</button>

		<div class="converter__output-frame">
			<div class="converter__output">
				<div class="converter__output-text">
					{{ valueFeet }}
				</div>

				<div class="converter__input-unit">
					ft
				</div>
			</div>
		</div>
	</section>

		<!-- <div class="converter__input-frame-advanced__info">
			<div>currentResult: {{ currentResult }}</div>
			<div>currentInput: {{ `"${currentInput}"` || `""` }}</div>
			<div>currentInputAsNumber: {{ currentInputAsNumber }}</div>
			<div>currentOperator: {{ currentOperator || `""` }}</div>
		</div> -->
	
</template>

<script>
	export default {
		data() {
			return {
				currentInput: 1,
			}
		},

		created() {
			window.addEventListener('keyup', this.handleKeyup);
			window.addEventListener('keydown', this.handleKeydown);
		},
		
		computed: {
			currentInputAsNumber() {
				return Number(this.currentInput)
			},
			valueFeet() {
				return (this.currentInput * 3.28)
			}
		},

		methods: {
			backSpaceResult() {
				// Bendik solution in comment, worked too
				// this.currentInput = this.currentInput.slice(0, this.currentInput.length-1);
				this.currentInput = this.currentInput.slice(0, -1);
			},
			
			clearResult() {
				this.currentInput = '';
			},

			handleDigitInput(digit) {
				this.currentInput += digit;
				this.showingResult = false;
			},

			handleKeyup(event) {
				switch(event.key) {
					case '0':
					case '1':
					case '2':
					case '3':
					case '4':
					case '5':
					case '6':
					case '7':
					case '8':
					case '9':
						this.handleDigitInput(event.key)
						break;
					case '.':
					case ',':
						this.handleDigitInput('.')
						break;
					case 'Escape':
						this.clearResult()
						break;
				}
			},

			handleKeydown(event) {
				switch(event.key) {
					case 'Backspace':
						this.backSpaceResult()
						break;
				}
			}
		}
	}
</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Inter&display=swap');

	:root {
		--button-background: #D9D9D9;;
		--button-hover: #B6B6B6;
		--double-button-background: #1E4FFB;
		--double-button-hover: #0E35C2;
	}

	* {
		box-sizing: border-box;
		margin: 0;
		padding: 0;
	}

	/* .converter {
		position: fixed;
		width: 25.4rem;
		height: 17.65rem;
		top: 382px;
		left: 610px;
		background: grey;
	} */
	
	.converter__input-frame {
		position: fixed;
		top: 34.1%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 25.4rem;
		height: 6.55rem;
		background: #EEEEEE;
		padding: 12px;
		border-radius: 1.75rem;
		box-shadow: 4px 4px 4px rgba(0, 0, 0, 0.25);
		font-family: 'Inter';
	}

	
	.converter__input {
		position: fixed;
		font-size: 2.75em;
		width: 20.15rem;
		height: 5.35rem;
		background: white;
		border-radius: 1.211rem;
		padding: .5em;
		border: none;
		margin-bottom: 1rem;
		overflow: hidden;
	}

	.converter__input-text {
		text-align: right;
		left: 110%;
	}

	.converter__input-unit {
		position: fixed;
		right: 5%;
		bottom: 19%;
	}
	
	.converter__output-frame {
		position: fixed;
		top: 54%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 25.4rem;
		height: 6.55rem;
		background: #EEEEEE;
		padding: 12px;
		border-radius: 1.75rem;
		box-shadow: 4px 4px 4px rgba(0, 0, 0, 0.25);
		font-family: 'Inter';
	}
	
	.converter__output {
		position: relative;
		font-size: 2.75em;
		width: 20.15rem;
		height: 5.35rem;
		background: white;
		border-radius: 1.211rem;
		padding: .5em;
		border: none;
		margin-bottom: 1rem;
		overflow: hidden;
	}

	.converter__output-text {
		text-align: right;
	}

	.converter__output-unit {
		position: fixed;
		right: 5%;
		bottom: 19%;
	}

	.switch-icon {
		position: fixed;
		top: 42.5%;
		left: 62%;
		/* transform: translate(-50%, -50%); */
	}

	.switch-icon img {
		width: 48px;
	}
	
</style>