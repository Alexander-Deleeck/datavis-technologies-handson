<script>
    import Scatterplot from "./Scatterplot.svelte"; 
    import {onMount} from 'svelte';

    let data = null; // initialize data object
    onMount(async() => {
        const res = await fetch('/data/gapminder.json') // load the data into result
        let data_temp = await res.json() // convert to json

        data = data_temp.find(datapoint => datapoint.year == '1800')['countries']; // Get data for countries in year 1800
    })
</script>

{#if data == null}
    <p>The data is being loaded</p>
{:else}
    <Scatterplot datapoints={data} />
{/if}
