<script>
  import { DataTable } from 'carbon-components-svelte';
  import SaveData from './SaveData.svelte';

  export let tempo;
  export let minim;
  export let quarter;
  export let eighthNote;
  export let eightDotted;
  export let semiQuaver;
  export let demiSemiQuaver;
  export let hemidemiSemiQuaver;
  export let oneHundredTwentyEight;

  // $: notes = [
  //   { note: 'BPM', value: tempo },
  //   { note: '1/2', value: minim },
  //   { note: '1/4', value: quarter },
  //   { note: '1/8', value: eighthNote },
  //   { note: '1/8T', value: eightDotted },
  //   { note: '1/16', value: semiQuaver },
  //   { note: '1/32', value: demiSemiQuaver },
  //   { note: '1/64', value: hemidemiSemiQuaver },
  //   { note: '1/128', value: oneHundredTwentyEight },
  // ];

  $: data = [
    {
      id: 1,
      bpm: tempo,
      '1/2': minim,
      '1/4': quarter,
      '1/8': eighthNote,
      '1/8T': eightDotted,
      '1/16': semiQuaver,
      '1/32': demiSemiQuaver,
      '1/64': hemidemiSemiQuaver,
      '1/128': oneHundredTwentyEight,
    },
  ];
</script>

<!-- <table style="width: 750px">
  <tr>
    {#each notes as note}
      <td>{note.note}</td>
    {/each}
  </tr>
  <tr>
    {#each notes as note}
      <td>{note.value}</td>
    {/each}
  </tr>
</table> -->

<DataTable
  headers={[
    { key: 'bpm', value: 'BPM' },
    { key: '1/2', value: '1/2' },
    { key: '1/4', value: '1/4' },
    { key: '1/8', value: '1/8' },
    { key: '1/8T', value: '1/8T' },
    { key: '1/16', value: '1/16' },
    { key: '1/32', value: '1/32' },
    { key: '1/64', value: '1/64' },
    { key: '1/128', value: '1/128' },
  ]}
  rows={data}
  style="margin-bottom: 20px;"
/>

<SaveData
  {data}
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
