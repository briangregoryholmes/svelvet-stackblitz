<script lang="ts">
	import { Svelvet, ThemeToggle, Group } from 'svelvet';
	import type { Theme } from 'svelvet';
	import Thickness from '../test-components/Thickness.svelte';
	import Noise from '../test-components/Noise.svelte';
	import Scale from '../test-components/Scale.svelte';
	import CircleColor from '../test-components/CircleColor.svelte';
	import DashCount from '../test-components/DashCount.svelte';
	import Output from '../test-components/Output.svelte';

	let zoom = 0.5;
</script>

<body>
	<Svelvet edgeStyle="step" TD {zoom} minimap controls>
		<Group
			position={{ x: -150, y: -100 }}
			width={600}
			height={700}
			color="goldenrod"
			groupName="parameters"
		>
			<Thickness />
			<Noise />
			<Scale />
			<CircleColor />
			<DashCount />
		</Group>
		<Output />
		<span id="state" class="note"> Stateful Anchors</span>
		<span id="groups" class="note">Group Boxes</span>
		<ThemeToggle main="dark" alt="light" slot="toggle" />
	</Svelvet>
</body>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Reenie+Beanie&display=swap');
	body {
		display: flex;
		justify-content: center;
		align-items: center;
		background-color: gray;
		width: 100vw;
		height: 100vh;
		padding: 0;
		margin: 0;
	}
	.note {
		font-family: 'Reenie Beanie', sans-serif;
		position: absolute;
		color: inherit;
		width: 400px;
		transform: rotate(-3deg);
		font-weight: 200px;
		font-size: 40px;
	}
	#state {
		top: -30px;
		left: 620px;
	}
	#groups {
		top: 530px;
		left: 490px;
	}
</style>
