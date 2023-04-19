<script>
  import { DataTable, Button } from 'carbon-components-svelte';
  import Save from 'carbon-icons-svelte/lib/Save.svelte';

  export let data;
  export let tempo;
  export let minim;
  export let quarter;
  export let eighthNote;
  export let eightDotted;
  export let semiQuaver;
  export let demiSemiQuaver;
  export let hemidemiSemiQuaver;
  export let oneHundredTwentyEight;

  let newData = [];

  const storeData = () => {
    if (newData.length === 0) {
      newData.push(data[0]);
      newData = newData;
      console.log(newData);
    } else {
      newData = [
        ...newData,
        {
          id: newData[newData.length - 1].id + 1,
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
    }
  };
</script>

<Button size="sm" icon={Save} on:click={storeData}>store</Button>

<h2 class="store">Convert Storage</h2>
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
  rows={newData}
  style="margin-bottom: 100px"
/>

<style>
  .store {
    font-size: 30px;
    font-weight: 700;
    margin: 30px 0 10px 0;
  }
</style>
