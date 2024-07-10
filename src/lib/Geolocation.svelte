<script>
    var mozgeos;
    var sysgeos = false;
    var disregupd;
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    function next() {
        var addedData = [["geo.provider.ms-windows-location", sysgeos], ["geo.provider.use_corelocation", sysgeos], ["geo.provider.use_gpsd", sysgeos], ["geo.provider.geoclue.always_high_accuracy", sysgeos], "geo.provider.use_geoclue", sysgeos];
        if (mozgeos) {
            addedData.push(["geo.provider.network.url", ""]);
        }
        if (disregupd) {
            addedData.push(["browser.region.network.url", ""], ["browser.region.update.enabled", false])
        }
        dispatch("next", addedData);
    }
</script>

<h2>Geolocation</h2>
<p>
    To not send data to google, you can use Mozilla's geolocation service by
    turning the following switch on. Warning! This installation doesnt support OS's geolocation service;
</p>
<div class="form-check form-switch aligned-left">
    <input
        class="form-check-input"
        type="checkbox"
        id="mozgeos"
        bind:checked={mozgeos}
    />
    <label class="form-check-label" for="mozgeos">
        Mozzila Geolocation Service
    </label>
</div>
<br>
<p>You can also disable region updates</p>
<div class="form-check form-switch aligned-left">
    <input
        class="form-check-input"
        type="checkbox"
        id="disregupd"
        bind:checked={disregupd}
    />
    <label class="form-check-label" for="disregupd">
        Disable Region Updates
    </label>
</div>
<button type="button" class="btn btn-primary" on:click={next}>Next</button>