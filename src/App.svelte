<script>
	import Nav from "./templates/Nav.svelte";
	import { onMount } from "svelte";
	export let name;

	let canvas;

	onMount(() => {
		canvas.width = window.innerWidth;
		canvas.height = window.innerHeight;
		const ctx = canvas.getContext('2d');
		ctx.beginPath();
		ctx.arc(100, 100, 2, 0, 2 * Math.PI);
		ctx.fillStyle = "#5e5e5e";
		ctx.fill();
		// mapCanvas(50)
	})

	function mapCanvas(count) {
		const ctx = canvas.getContext('2d');
		for(let i = 0; i <= count; i++) {
			ctx.beginPath();
			ctx.arc(
				Math.round(Math.random() * window.innerWidth), 
				Math.round(Math.random() * window.innerHeight), 
				2, 0, 2 * Math.PI
				);
			ctx.fillStyle = "#5e5e5e";
			ctx.fill();
		}
	}

	function animateCanvas() {
		requestAnimationFrame(animate)
	}
</script>

<main>
	<canvas bind:this={canvas}></canvas>
	<h1>{name}</h1>
	<Nav />
</main>

<style>
	main {
		background-color: #141414;
		height: 100vh;
		text-align: center;
		max-width: 240px;
		margin: 0 auto;
	}

	canvas {
		position: absolute;
		top: 0;
		left: 0;
	}

	h1 {
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 700;
		margin: 0;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>