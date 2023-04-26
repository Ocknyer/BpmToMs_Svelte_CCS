<script>
  import { DataTable } from 'carbon-components-svelte';

  export let setlist;
</script>

<div>
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
    rows={setlist[0]}
  />
</div>
