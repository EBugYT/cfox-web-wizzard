<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    function next() {
        dispatch("next", []);
    }
</script>

<h2>Welcome to CFox Web Wizzard</h2>
<p>Here you can build a privacy enforced custom Firefox client. Most settings are set to firefox default, but you can set them to whatever you want</p>
<button type="button" class="btn btn-primary" on:click={next}>Start</button>
