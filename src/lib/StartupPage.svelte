<script>
    var stpage = "1";
    var homeurl = "about:home";
    var assc = true;
    var actstreamnp = true;
    var ddts;
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    function next() {
        var addedData = [
            ["browser.startup.page", stpage],
            ["browser.startup.homepage", homeurl],
            ["browser.newtabpage.enabled", actstreamnp],
            ["browser.newtabpage.activity-stream.showSponsored", assc],
            ["browser.newtabpage.activity-stream.showSponsoredTopSites", assc]
        ];
        if (ddts) {
            addedData.push(["browser.newtabpage.activity-stream.default.sites", ""])
            addedData.push(["browser.topsites.contile.enabled", false])
            addedData.push(["browser.topsites.useRemoteSetting", false])
        }
        dispatch("next", addedData);
    }
</script>

<h2>Startup Page/New Tab settings</h2>
<p>
    A startup page is a page that appears when you start up firefox. Use the
    following dropdown menu to change it
</p>
<select class="form-select" bind:value={stpage}>
    <option selected disabled>Startup page</option>
    <option value="0">Blank page</option>
    <option value="1">Homepage</option>
    <option value="2">Last visited website</option>
    <option value="3">Resume previous session</option>
</select>
<br />
<p>
    The "homepage" option can mean whatever url you select. Enter the url you
    want to be the "homepage". This option will also be the url opened when you
    click the hamburger menu and New Window or hit Ctrl+N
</p>
<p>
    Examples: about:blank for a blank page, about:home for the default "Activity
    Stream" homepage, start.duckduckgo.com for duckduckgo etc.
</p>
<input type="text" bind:value={homeurl} class="form-control" />
<br />

<div class="form-check form-switch aligned-left">
    <input
        class="form-check-input"
        type="checkbox"
        id="actstreamnp"
        bind:checked={actstreamnp}
    />
    <label class="form-check-label" for="actstreamnp">
        {actstreamnp
            ? "New tab page: Activity Stream"
            : "New tab page: Blank page"}
    </label>
</div>

<br />
<div class="form-check form-switch aligned-left">
    <input
        class="form-check-input"
        type="checkbox"
        id="assc"
        bind:checked={assc}
    />
    <label class="form-check-label" for="assc">
        Sponsored content on Activity Stream homepage
    </label>
</div>

<div class="form-check form-switch aligned-left">
    <input
        class="form-check-input"
        type="checkbox"
        id="ddts"
        bind:checked={ddts}
    />
    <label class="form-check-label" for="ddts">
        Disable default topsites
    </label>
</div>

<button type="button" on:click={next} class="btn btn-primary">Next</button>
