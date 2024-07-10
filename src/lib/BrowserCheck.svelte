<script>
    var dbc = true;
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    
    function next() {
        dispatch("next", [["browser.shell.checkDefaultBrowser", dbc]])
    }
</script>

<h2>Default Browser Check</h2>
<p>Defaultly, Firefox always checks if it's the default browser. Use the following checkbox to disable it.</p>
<div class="form-check form-switch aligned-left">
    <input type="checkbox" id="dbc" class="form-check-input" bind:checked={dbc}>
    <label for="dbc" class="form-check-label">Check if Firefox is the default browser</label>
</div>

<button type="button" class="btn btn-primary" on:click={next}>Next</button>