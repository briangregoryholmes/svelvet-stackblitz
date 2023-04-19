<script lang="ts">
	export let size = 200;
	export let strokeWidth = 4;
	export let dashFactor = 5;
	export let numCircles = 30;
	export let spacing = 0;
	export let color = 'red';
	export let noise = 0; // Add noise parameter

	interface Circle {
		cx: number;
		cy: number;
		r: number;
		strokeWidth: number;
		dashArray: string;
		angle: number;
	}

	let circles: Array<Circle> = [];
	let previousNoiseFactor = 0;
	let previousNoise = 0;
	let dashLength;
	let gapLength;
	$: animate = spacing;

	$: {
		circles = generateCircles(size, strokeWidth, dashFactor, numCircles, spacing, noise);
	}

	const random = Array(50)
		.fill(null)
		.map((_, i) => 1 - Math.random());

	function generateCircles(
		size: number,
		strokeWidth: number,
		dashFactor: number,
		numCircles: number,
		spacing: number,
		noise: number
	) {
		let generatedCircles = [];

		for (let i = 0; i < numCircles; i++) {
			const noiseFactor = noise * random[i];
			let radius = size * (i / numCircles) * 2;
			let angle = 0;
			let circumference = 2 * Math.PI * radius;
			dashLength = circumference / dashFactor / 2;
			gapLength = (circumference - dashLength) / (dashFactor - 1);

			dashLength += random[i] * noise * 5;
			angle = 1440 * random[i] * noise;
			// console.log({ angle, noiseFactor, i });
			strokeWidth += (random[i] * noise) / 2;

			let circle = {
				cx: size / 2,
				cy: size / 2,
				r: radius,
				strokeWidth: strokeWidth,
				dashArray: `${dashLength},${dashLength}`,
				angle
			};

			generatedCircles.push(circle);
			radius += spacing;
		}
		previousNoise = noise;
		return generatedCircles;
	}
</script>

<svg width="100%" height="100%" xmlns="http://www.w3.org/2000/svg">
	{#each circles as circle (circle.r)}
		<circle
			cx="50%"
			cy="50%"
			r={circle.r}
			style:--animation-speed={spacing + 's'}
			stroke={color}
			style:transform-origin="50% 50%"
			style:transform={`rotate(${circle.angle}deg)`}
			fill="none"
			stroke-width={circle.strokeWidth}
			stroke-dasharray={circle.dashArray}
			class:animate
		/>
	{/each}
</svg>

<style>
	svg {
		pointer-events: auto;
	}

	.animate {
		animation: dash var(--animation-speed) linear infinite;
	}

	@keyframes dash {
		to {
			stroke-dashoffset: -1000;
			stroke-dasharray: 100;
		}
	}
</style>
