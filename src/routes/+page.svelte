<script>
	// @ts-nocheck

	let num1;
	let num2;
	let operation;

	let total = 0;
	let keyPressed;

	let display = '';

	function clear() {
		display = '';
		total = 0;
		num1 = '';
		num2 = '';
		operation = '';
	}

	// @ts-ignore
	function handleClick(button) {
		keyPressed = button.target.innerText;
		switch (keyPressed) {
			case '+':
				operation = '+';
				num1 = parseFloat(display);
				display = '';

				console.log(num1);

				break;
			case '-':
				operation = '-';
				num1 = parseFloat(display);
				display = '';

				break;
			case 'x':
				operation = 'x';
				num1 = parseFloat(display);
				display = '';

				break;
			case '÷':
				operation = '÷';
				num1 = parseFloat(display);
				display = '';

				break;
			case '=':
				num2 = parseFloat(display);

				switch (operation) {
					case '+':
						total = num1 + num2;
						break;
					case '-':
						total = num1 - num2;
						break;

					case 'x':
						total = num1 * num2;
						break;
					case '÷':
						total = num1 / num2;
						break;
				}
				display = total.toString();
				operation = '';
				break;
			default:
		}
		if (keyPressed === '=') {
		}

		if (
			keyPressed == 0 ||
			keyPressed == 1 ||
			keyPressed == 2 ||
			keyPressed == 3 ||
			keyPressed == 4 ||
			keyPressed == 5 ||
			keyPressed == 6 ||
			keyPressed == 7 ||
			keyPressed == 8 ||
			keyPressed == 9 ||
			keyPressed == '.'
		) {
			display = display + keyPressed;
		}
	}
</script>

<div class="calculator">
	<input type="text" bind:value={display} />
	<div class="buttons">
		<div class="operations">
			<button on:click={handleClick}> + </button>
			<button on:click={handleClick}> - </button>
			<button on:click={handleClick}> x </button>
			<button on:click={handleClick}> ÷ </button>
		</div>
		<div class="numbers">
			<div>
				<button on:click={handleClick}> 7 </button>
				<button on:click={handleClick}> 8 </button>
				<button on:click={handleClick}> 9 </button>
			</div>
			<div>
				<button on:click={handleClick}> 4 </button>
				<button on:click={handleClick}> 5 </button>
				<button on:click={handleClick}> 6 </button>
			</div>
			<div>
				<button on:click={handleClick}> 1 </button>
				<button on:click={handleClick}> 2 </button>
				<button on:click={handleClick}> 3 </button>
			</div>
			<div>
				<button on:click={handleClick}> 0 </button>
				<button on:click={handleClick}> . </button>
				<button class="clear" on:click={clear}> Clear </button>
			</div>
		</div>
		<div class="equal">
			<button on:click={handleClick}> = </button>
		</div>
	</div>
</div>

<style>
	.calculator .buttons .clear {
		color: #eee;
		background-color: crimson;
	}
	.calculator {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 300px;
		border: 1px solid #eee;
		box-shadow: 2px 2px 2px #eee;
		padding: 10px;
	}
	.calculator input {
		width: 256px;
		padding: 20px;
		outline: none;
		text-align: right;
		font-size: 20px;
	}
	.calculator .buttons {
		display: flex;
		flex-wrap: wrap;
	}
	.calculator .buttons .operations {
		display: flex;
		justify-content: space-between;
		width: 100%;
	}
	.calculator .buttons .operations button {
		width: 24%;
	}
	.calculator .buttons .numbers {
		width: 75%;
	}
	.calculator .buttons .numbers > div {
		display: flex;
		justify-content: space-between;
	}
	.calculator .buttons .numbers > div button {
		width: 32%;
	}
	.calculator .equal {
		flex: 1;
	}
	.calculator .equal button {
		margin-left: 5%;
		width: 95%;
		height: 95%;
		background: #00acee;
		color: #eee;
	}
	.calculator button {
		outline: none;
	}
</style>
