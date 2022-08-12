
<script lang="ts">
	import { spring } from 'svelte/motion';
	import { Confetti } from "svelte-confetti";
	import ToggleConfetti from './ToggleConfetti.svelte';
	import ConfettiOnClick from './ConfettiOnClick.svelte';
	let count = 0;

	const displayed_count = spring();
	$: displayed_count.set(count);
	$: offset = modulo($displayed_count, 1);

	function modulo(n: number, m: number) {
		// handle negative numbers
		return ((n % m) + m) % m;
	}

	function decrease() {
	
	(count -= 1);
	
	
	}

</script>

<div class="counter">
	<ToggleConfetti>
		<button  on:click={() => (count -= 5)} slot="label">-5
	
		</button>
	
		<Confetti x={[-1, -0.25]} y={[0, 0.5]} />
	</ToggleConfetti>

	<ToggleConfetti>
		<button  on:click={decrease} slot="label">-
	
		</button>
	
		<Confetti x={[-0.25, 0.25]} y={[-0.75, -0.25]} />
	</ToggleConfetti>



	<div class="counter-viewport">
		<div class="counter-digits" style="transform: translate(0, {100 * offset}%)">
			<strong class="hidden" aria-hidden="true">{Math.floor($displayed_count + 1)}</strong>
			<strong>{Math.floor($displayed_count)}</strong>
		</div>
	</div>

	<ToggleConfetti>
		<button  on:click={() => (count += 1)} slot="label">+
	
		</button>
	
		<Confetti x={[-0.25, 0.25]} y={[0.75, 1.5]} />
	</ToggleConfetti>


	<ToggleConfetti>
		<button  on:click={() => (count += 5)} slot="label">+5
	
		</button>
	
		<Confetti x={[0.25, 1]} y={[0, 0.5]} />
	</ToggleConfetti>


	
	


</div>




<style>
	.counter {
		display: flex;
		border-top: 1px solid rgba(0, 0, 0, 0.1);
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		margin: 1rem 0;
	}

	.counter button {
		width: 2em;
		padding: 0;
		display: flex;
		align-items: center;
		justify-content: center;
		border: 0;
		background-color: transparent;
		touch-action: manipulation;
		color: var(--text-color);
		font-size: 2rem;
	}

	.counter button:hover {
		background-color: var(--secondary-color);
	}

	


	.counter-viewport {
		width: 8em;
		height: 4em;
		overflow: hidden;
		text-align: center;
		position: relative;
	}

	.counter-viewport strong {
		position: absolute;
		display: flex;
		width: 100%;
		height: 100%;
		font-weight: 400;
		color: var(--accent-color);
		font-size: 4rem;
		align-items: center;
		justify-content: center;
	}

	.counter-digits {
		position: absolute;
		width: 100%;
		height: 100%;
	}

	.hidden {
		top: -100%;
		user-select: none;
	}
</style>
