<script>
  // IMPORT
  import { onMount } from "svelte";

  // IMPORT COMPONENTS
  import Date from "./lib/Date.svelte";
  import TaskAdd from "./lib/TaskAdd.svelte";
  import TaskList from "./lib/TaskList.svelte";

  // DECLARE VARIABLES
  let allTasks = [];

  // RETRIEVE EXISTING TASKS FROM LOCAL STORAGE
  onMount(() => {
    let localTasks = JSON.parse(window.localStorage.getItem("allTasks"));
    if (!localTasks) {
      return;
    } else {
      return (allTasks = localTasks);
    }
  });

  // CHECKED TASK
  const onCheck = (task) => {
    task.complete = !task.complete;
  };
</script>

<main>
    <div class="wrapper">
      <Date />
      <TaskAdd bind:allTasks />
      <TaskList bind:allTasks />
    </div>
</main>

<style>
  /* TBD */
</style>
