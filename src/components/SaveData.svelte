<script>
  import {
    DataTable,
    Button,
    Modal,
    TextInput,
  } from 'carbon-components-svelte';
  import Save from 'carbon-icons-svelte/lib/Save.svelte';
  import Reset from 'carbon-icons-svelte/lib/Reset.svelte';
  import SetList from './SetList.svelte';

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
  let setlist = [];

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

  const resetData = () => {
    if (newData) {
      newData = [];
    }
  };

  let open = false;

  const storeSetlist = () => {
    if (newData.length) {
      setlist.push(newData);
      setlist = setlist;
      open = true;
      console.log(setlist);
    }
  };

  let list = '';

  $: set = [{ songName: '', setlist: {} }];

  const setSongList = () => {
    set[0].songName = list;
    set[0].setlist = [...setlist];
    open = false;
  };

  $: {
    console.log(set);
  }
</script>

<div class="btn-box">
  <Button
    size="sm"
    iconDescription="store converted data"
    icon={Save}
    on:click={storeData}>store</Button
  >
  <Button
    size="sm"
    kind="danger"
    iconDescription="reset data"
    icon={Reset}
    on:click={resetData}>reset</Button
  >
</div>

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

<Button size="sm" on:click={storeSetlist}>Store Set Lists</Button>

<Modal
  bind:open
  hasForm
  modalHeading="Add set list name"
  primaryButtonText="Confirm"
  secondaryButtonText="Cancel"
  selectorPrimaryFocus="#db-name"
  shouldSubmitOnEnter
  on:click:button--secondary={() => (open = false)}
  on:click:button--primary={setSongList}
  on:open
  on:close
  on:submit
>
  <p>Create a new set list</p>
  <br />
  <TextInput
    id="db-name"
    labelText="Set list name"
    placeholder="Enter set list name..."
    bind:value={list}
  />
</Modal>

<SetList {setlist} />

<style>
  .btn-box {
    display: flex;
    gap: 12px;
  }

  .store {
    font-size: 30px;
    font-weight: 700;
    margin: 30px 0 10px 0;
  }
</style>
