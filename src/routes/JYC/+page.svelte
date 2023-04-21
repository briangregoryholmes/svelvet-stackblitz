<script lang="ts">
	import { Svelvet, Node, Background } from 'svelvet';
</script>

<Svelvet width={800} height={600} minimap>
	<Node />
	<Background slot="background" bgColor="transparent" />
</Svelvet>

<style>
	:global(html) {
		background-color: black;
	}
</style>
