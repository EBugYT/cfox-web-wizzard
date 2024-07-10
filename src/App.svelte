<script>
    import Welcome from "./lib/Welcome.svelte";
    import Aboutcw from "./lib/Aboutcw.svelte";
    import BrowserCheck from "./lib/BrowserCheck.svelte";
    import StartupPage from "./lib/StartupPage.svelte";
    import Geolocation from "./lib/Geolocation.svelte";
    var scene = 1;
    var abtConfigArr = {}
    function next(e) {
        scene++;
        addToAbtConfigArr(e.detail)
    }
    function addToAbtConfigArr(e) {
        e.forEach(el => {
            abtConfigArr[el[0]] = el[1]
        });
        console.log(abtConfigArr)
    }
</script>

{#if scene == 1}
    <Welcome on:next={next} />
{:else if scene == 2}
    <Aboutcw on:next={next} />
{:else if scene == 3}
    <BrowserCheck on:next={next} />
{:else if scene == 4}
    <StartupPage on:next={next} />
{:else if scene == 5}
    <Geolocation on:next={next} />
{/if}
