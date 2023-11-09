<script>
    // IMPORTS
    import { onMount } from "svelte";

    // CURRENT DATE
    let date_full = new Date().toLocaleDateString("en-us", {
        month: "long",
        day: "numeric",
        year: "numeric",
    });
    let date_day = new Date().toLocaleDateString("en-us", {
        weekday: "long",
    });
    let time = new Date().toLocaleTimeString("en-us", {
        hour: "2-digit",
        minute: "2-digit",
    });

    //DECLARE FUNCTIONS
    onMount(() => {
        const interval = setInterval(() => {
            time = new Date().toLocaleTimeString("en-us", {
                hour: "2-digit",
                minute: "2-digit",
            });
        }, 1000);

        return () => {
            clearInterval(interval);
        };
    });
</script>

<div class="card-date">
    <h1>
        {date_full}
    </h1>
    <h2>
        {date_day}
    </h2>
    <h3>
        {time}
    </h3>
</div>