<script>
  // DECLARE VARIABLES
  export let allTasks = [];

  // DELETE TASK
  export const onDelete = (e) => {
    allTasks = allTasks.filter((task) => {
      return task.id !== e.id;
    });
    window.localStorage.setItem("allTasks", JSON.stringify(allTasks));
  };

  // CHECKED TASK
  export const onCheck = (task) => {
    task.complete = !task.complete;
  };
</script>

<ul>
  {#each allTasks as task (task.id)}
    <li class:completed-item={task.complete}>
      <div class="card-task">
        <input
          type="checkbox"
          on:click={() => onCheck(task)}
          bind:checked={task.complete}
        />
        <div>
          {task.name}
        </div>
        <button class="btn-delete" on:click={() => onDelete(task)}>
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-5 h-5">
            <path d="M6.28 5.22a.75.75 0 00-1.06 1.06L8.94 10l-3.72 3.72a.75.75 0 101.06 1.06L10 11.06l3.72 3.72a.75.75 0 101.06-1.06L11.06 10l3.72-3.72a.75.75 0 00-1.06-1.06L10 8.94 6.28 5.22z" />
          </svg>                  
        </button>
      </div>
    </li>
  {/each}
</ul>

<style>
  /* TBD */
</style>