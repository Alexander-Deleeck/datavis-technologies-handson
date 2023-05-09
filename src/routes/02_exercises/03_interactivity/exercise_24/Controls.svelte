<script>
  import Exercise from "./Exercise.svelte";

  // Dimensions
  const [height, width] = [400, 550];
  const margin = { top: 50, right: 5, bottom: 55, left: 50 };
  const innerWidth = width - margin.left - margin.right;
  const innerHeight = height - margin.top - margin.bottom;

  // Properties
  const continents = ["europe", "asia", "americas", "africa"];
  export let selected_continents = []; // this will become the array that holds the selected continents

  export let index_control = 0; // this 
  let playing = false; // This will become the play pause button
  let countYear; // this variable will represent the current year that is being displayed

  function playPause(){
    if (playing == true){
      clearInterval(countYear)
    }else{
      countYear = setInterval(increaseYear, 70);
    }
    playing = !playing
  }

  function increaseYear(){
    index_control += 1
    if (index_control > 214){ //214 is max because year index starts as 0 meaning 1800 whereby 214 represents 2014
      resetYear()
    }
  }

  function resetYear(){
    index_control = 0;
  }

</script>


<div class="controls-group-row" viewBox="0 0 {width} {height}" style="max-width: {width}px">
  <div class="controls-group-column">
    <button on:click={playPause}>Play Pause</button>
    <button on:click={resetYear}>Reset</button>
    <div>
      <h5>Year:</h5>
      <input type="range" min="0" max="214" bind:value={index_control}> {index_control + 1800}
    </div>
  </div>
  <div class="controls-group-column">
    <h5>Continents:</h5>
    <select name='regions' id="continents_checkbox" selected_continents = "selected">
    {#each continents as continent}
      <option>
        {continent}
      </option>
    {/each}
  </select>
  </div>
</div>

<style>
  .controls-group-row {
    text-align: center;
    
  }
  .controls-group-row button {
    background-color: #04AA6D;
    border: 1px solid green; /* Green border */
    color: white; /* White text */
    margin: 10px;
    padding: 10px 24px;
  }

  .controls-group-column {
    float: left;
    width: 50%;
  }

  .controls-group-row:after {
    content: "";
    display: table;
    clear: both;
  }

  #continents_checkbox {
    margin-left: 70px;
  }

  #continents_checkbox label {
    display: block;
    text-align: left;
  }
</style>