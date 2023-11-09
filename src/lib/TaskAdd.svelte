<script>
  // DECLARE VARIABLES
  export let allTasks = [];

  // ADD TASK
  const onSubmit = (e) => {
    let inputValue = e.target[0].value;
    if (allTasks.length >= 5) {
      alert(
        "Woah, that list is looking pretty long! You sure you don't want to complete a few of these first? 🤔"
      );
      return;
    } else {
      if (inputValue) {
        let newTask = {
          id: allTasks.length + 1,
          name: inputValue,
          complete: false,
        };
        allTasks = [newTask, ...allTasks];
        window.localStorage.setItem("allTasks", JSON.stringify(allTasks));
        e.target.reset();
      } else {
        alert("Please add a task! 🚨");
      }
    }
  };
</script>

<div class="card">
  <form on:submit|preventDefault={onSubmit}>
    <label for="task">
      <!-- svelte-ignore a11y-autofocus -->
      <input id="task" name="task" autocomplete="off" />
    </label>
    <button class="btn-add" type="submit">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 20 20"
        fill="currentColor"
        class="w-5 h-5"
      >
        <path
          d="M10.75 4.75a.75.75 0 00-1.5 0v4.5h-4.5a.75.75 0 000 1.5h4.5v4.5a.75.75 0 001.5 0v-4.5h4.5a.75.75 0 000-1.5h-4.5v-4.5z"
        />
      </svg>
    </button>
  </form>
</div>

<style>
  /* TBD */
</style>
