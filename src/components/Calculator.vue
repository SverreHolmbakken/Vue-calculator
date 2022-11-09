<template>
	<div class="title">
		<h1 class="title__text">Kalkis</h1>
	</div>
	
	<section class="calculator">
		<div class="calculator__output">
			<div class="calculator__output-text">
				{{ showingResult ? currentResult : currentInput }}
			</div>
		</div>

		<div class="calculator__buttons">
			<button @click="backSpaceResult" class="calculator__button calculator__operator"><img src="../assets/icons/Backspace-button.svg" alt=""></button>
			<button @click="clearResult" class="calculator__button calculator__operator">CE</button>
			<button @click="handleOperatorInput('/')" class="calculator__button calculator__operator">÷</button>
			<button @click="handleOperatorInput('*')" class="calculator__button calculator__operator">×</button>
			<button @click="handleDigitInput(7)" class="calculator__button calculator__digit">7</button>
			<button @click="handleDigitInput(8)" class="calculator__button calculator__digit">8</button>
			<button @click="handleDigitInput(9)" class="calculator__button calculator__digit">9</button>
			<button @click="handleOperatorInput('-')" class="calculator__button calculator__operator">-</button>
			<button @click="handleDigitInput(4)" class="calculator__button calculator__digit">4</button>
			<button @click="handleDigitInput(5)" class="calculator__button calculator__digit">5</button>
			<button @click="handleDigitInput(6)" class="calculator__button calculator__digit">6</button>
			<button @click="handleOperatorInput('+')" class="calculator__button calculator__operator">+</button>
			<button @click="handleDigitInput(1)" class="calculator__button calculator__digit">1</button>
			<button @click="handleDigitInput(2)" class="calculator__button calculator__digit">2</button>
			<button @click="handleDigitInput(3)" class="calculator__button calculator__digit">3</button>
			<button @click="handleEqualsInput" class="calculator__button calculator__digit--sum">=</button>
			<button @click="handleDigitInput(0)" class="calculator__button calculator__digit--zero">0</button>
			<button @click="handleDigitInput('.')" class="calculator__button calculator__digit">,</button>

		</div>

		<!-- <div class="calculator-advanced__info">
			<div>currentResult: {{ currentResult }}</div>
			<div>currentInput: {{ `"${currentInput}"` || `""` }}</div>
			<div>currentInputAsNumber: {{ currentInputAsNumber }}</div>
			<div>currentOperator: {{ currentOperator || `""` }}</div>
		</div> -->
	</section>
</template>

<script>
	export default {
		data() {
			return {
				currentResult: 0,
				currentInput: '',
				currentOperator: null,
				showingResult: false,
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
		},

		methods: {
			calculateResult() {
				switch(this.currentOperator) {
					case '+':
						this.currentResult += this.currentInputAsNumber;
						break;
					case '-':
						this.currentResult -= this.currentInputAsNumber;
						break;
					case '/':
						this.currentResult /= this.currentInputAsNumber;
						break;
					case '*':
						this.currentResult *= this.currentInputAsNumber;
						break;
					default:
						this.currentResult = this.currentInputAsNumber;
				}
			},

			backSpaceResult() {
				// Bendik solution in comment, worked too
				// this.currentInput = this.currentInput.slice(0, this.currentInput.length-1);
				this.currentInput = this.currentInput.slice(0, -1);
			},
			
			clearResult() {
				this.currentResult = 0;
				this.currentInput = '';
				this.currentOperator = null;
				this.showingResult = false;
			},
			
			handleOperatorInput(operator) {
				this.calculateResult();
				this.currentOperator = operator;
				this.currentInput = '';
				this.showingResult = true;
			},

			handleDigitInput(digit) {
				this.currentInput += digit;
				this.showingResult = false;
			},
			
			handleEqualsInput() {
				this.calculateResult();
				this.showingResult = true;
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
					case '+':
					case '-':
					case '/':
					case '*':
						this.handleOperatorInput(event.key)
						break;
					case '.':
					case ',':
						this.handleDigitInput('.')
						break;
					case '=':
					case 'Enter':
						this.handleEqualsInput()
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

	.calculator {
		position: fixed;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 21.35rem;
		height: 32.8rem;
		background: #EEEEEE;
		padding: 12px;
		border-radius: 1.75rem;
		box-shadow: 4px 4px 4px rgba(0, 0, 0, 0.25);
		font-family: 'Inter';
	}

	
	.calculator__output {
		position: relative;
		font-size: 2.75em;
		width: 100%;
		height: 5.75rem;
		background: white;
		border-radius: 1.211rem;
		padding: .5em;
		border: none;
		margin-bottom: 1rem;
		overflow: hidden;
	}

	.calculator__output-text {
		text-align: right;
	}
	
	.calculator__buttons {
		display: grid;
		grid-template-rows: 1fr 1fr ;
		grid-template-columns: 1fr 1fr 1fr 1fr;
		border-radius: 1.211rem;
		gap: 0.6rem;
	}

	.calculator__button {
		border-radius: 1.211rem;
		padding: .5em;
		font-size: 2rem;
	}

	.calculator__digit--sum {
		background-color: var(--double-button-background);
		color: white;
		grid-row: 4/6;
		grid-column: 4;
	}

	.calculator__digit--zero {
		background-color: var(--double-button-background);
		color: white;
		grid-row: 5;
		grid-column: 1/3;
	}

	.calculator__digit {
		background-color: var(--button-background);
		border-radius: 1.211rem;
		height: 4.41rem;
		border: none;
	}

	.calculator__operator {
		background: var(--button-background);
		border-radius: 1.211rem;
		height: 4.41rem;
	}

	.calculator__digit:hover,
	.calculator__operator:hover{
		background: var(--button-hover);
	}

	.calculator__digit--sum:hover,
	.calculator__digit--zero:hover {
		background: var(--double-button-hover);
	}

	.calculator__digit:active,
	.calculator__operator:active {
		box-shadow: inset 4px 4px 4px rgba(0, 0, 0, 0.25);
	}

	.calculator__digit--sum:active,
	.calculator__digit--zero:active {
		box-shadow: inset 4px 4px 4px rgba(0, 0, 0, 0.25);
	}
</style>