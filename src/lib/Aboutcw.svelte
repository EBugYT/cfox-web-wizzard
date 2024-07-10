<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    var acw = true

    function next() {
        dispatch("next", [["browser.aboutConfig.showWarning", acw]])
    }
</script>

<h2>about:config warning</h2>
<p>By default, on the about:config page, there is a warning saying that changing settings on there can lower the performance and safety of firefox (what is not really true). By unchecking the following checkmark you can remove it.</p>
<div class="form-check form-switch aligned-left">
    <input class="form-check-input" type="checkbox" id="acws" bind:checked={acw}>
    <label for="acws" class="form-check-label">Warning on about:config</label>
</div>

<button type="button" class="btn btn-primary" on:click={next}>Next</button>