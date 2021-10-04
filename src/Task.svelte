<script lang="ts">
  import { createEventDispatcher } from 'svelte';

  let text: string;
  let finished = false;
  let disabled = true;

  const dispatch = createEventDispatcher();

  const deleteTask = () => {
    dispatch('delete');
  };

</script>


<input type="checkbox" bind:value={finished}>
<input bind:value={text} {disabled}>
<button on:click="{() => { disabled = !disabled; }}">Edit</button>
<button on:click={deleteTask}>Delete</button>