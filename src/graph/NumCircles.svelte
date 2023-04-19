<script lang="ts">
  import { Node, Anchor } from 'svelvet-test';
  import { generateInput, generateOutput, Slider } from 'svelvet-test';
  import NodeWrapper from './NodeWrapper.svelte';

  type Inputs = {
    num: number;
  };

  const initialData = {
    num: 27,
  };
  const inputs = generateInput(initialData);
  const procesor = (inputs: Inputs) => inputs.num;
  const output = generateOutput(inputs, procesor);
</script>

<Node position={{ x: -150, y: 190 }} let:selected>
  <NodeWrapper title="Scale" outputStore={output} key="numCircles">
    <div class="node-body">
      <Slider min={1} max={27} step={1} parameterStore={$inputs.num} />
    </div>
  </NodeWrapper>
</Node>

<style>
  .node-body {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>
