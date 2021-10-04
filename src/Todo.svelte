<script lang="ts">
  import Task from './Task.svelte';

  let completedTask = 0;
  let totalTask: number;

  const tasks: Array<Object> = [];

  // new task props
  const newTask = {
    text: undefined,
  };
  
  const addNewTask = () => {
    tasks.push(newTask);
  };

  $: totalTask = tasks.length;

  const deleteTask = (event: CustomEvent) => {
    tasks.splice(+event.detail.value, 1);
  };
</script>

<!--
1 - I'm gonna add a new created task to the already created tasks list.
2 - To achieve this, I can create an event handler responsible for doing this.
-->

<h2>What needs to be done?</h2>
<input bind:value={newTask.text} type="text" id="task">
<button on:click={addNewTask}>Add</button>

<div>
  <button>All</button>
  <button>Active</button>
  <button>Completed</button>
</div>

<h1>{completedTask} out of {totalTask} items completed.</h1>

{#each tasks as task}
  <Task {...task} on:delete={deleteTask}/>
{/each}

<divider></divider>

<div>
  <button>Check All</button>
  <button>Remove Completed</button>
</div>