<script>
  import { Button, NumberInput } from 'carbon-components-svelte';
  import Add from 'carbon-icons-svelte/lib/Add.svelte';
  import Subtract from 'carbon-icons-svelte/lib/Subtract.svelte';
  export let tempo;
  export let increase;
  export let decrease;
  export let editTempo;
  export let handleTempo;

  $: {
    console.log(tempo, typeof tempo);
  }
</script>

<div class="container">
  <Button
    iconDescription="Increase tempo"
    icon={Add}
    on:click={increase}
    style="display: block;"
  />
  <NumberInput
    min={0}
    max={300}
    invalid={tempo > 300 && tempo < 0 ? true : false}
    invalidText="BPM must be between 0 and 300"
    helperText="Type BPM to convert MS"
    bind:value={tempo}
    on:keyup={editTempo}
    on:click={handleTempo}
  />
  <Button
    iconDescription="Decrease tempo"
    icon={Subtract}
    on:click={decrease}
  />
</div>

<style>
  .container {
    display: flex;
    justify-content: center;
    margin: 30px 0;
    gap: 15px;
  }
</style>
