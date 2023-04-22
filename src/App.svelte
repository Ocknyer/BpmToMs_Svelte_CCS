<script>
  import 'carbon-components-svelte/css/all.css';
  import Input from './components/Input.svelte';
  import Table from './components/Table.svelte';
  import Header from './components/Header.svelte';
  import { Theme } from 'carbon-components-svelte';

  let tempo = 100;

  const increase = () => {
    if (tempo < 300) {
      tempo = tempo + 1;
    }
  };

  const decrease = () => {
    if (tempo > 0) {
      tempo = tempo - 1;
    }
  };

  const handleTempo = (e) => {
    if (e.target.title === 'Decrement number' && tempo < 300) {
      tempo = tempo - 1;
    }
    if (e.target.title === 'Increment number' && tempo > 0) {
      tempo = tempo + 1;
    }
  };

  let theme = 'white'; // "white" | "g10" | "g80" | "g90" | "g100"

  const editTempo = (e) => {
    tempo = parseInt(e.target.value);
  };

  $: baseBPM = 60000 / tempo;

  $: minim = Math.ceil(baseBPM) * 2 + 'ms';
  $: quarter = Math.ceil(baseBPM) + 'ms';
  $: eighthNote = Math.ceil(baseBPM / 2) + 'ms';
  $: eightDotted = Math.ceil(baseBPM / 3) + 'ms';
  $: semiQuaver = Math.ceil(baseBPM / 4) + 'ms';
  $: demiSemiQuaver = Math.ceil(baseBPM / 8) + 'ms';
  $: hemidemiSemiQuaver = Math.ceil(baseBPM / 16) + 'ms';
  $: oneHundredTwentyEight = Math.ceil(baseBPM / 32) + 'ms';
</script>

<Theme bind:theme persist persistKey="__carbon-theme" />

<Header {theme} />

<div id="app">
  <h1 class="title">BPM to MS</h1>
  <Input {tempo} {increase} {decrease} {editTempo} {handleTempo} />
  <Table
    {tempo}
    {minim}
    {quarter}
    {eighthNote}
    {eightDotted}
    {semiQuaver}
    {demiSemiQuaver}
    {hemidemiSemiQuaver}
    {oneHundredTwentyEight}
  />
</div>

<style>
  #app {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 100px auto;
  }

  .title {
    font-size: 42px;
    font-weight: 700;
  }
</style>
