<script>
  let data;
  let code;
  import * as Huffman from "./Huffman/Huffman.js";
  import Canvas from "./Components/Canvas.svelte";

  function apply() {
    const val = data.value;
    if (!val) return;
    code = null;
    code = Huffman.code(val);
  }

  function reset() {
    code = null;
  }
</script>

<style>
  header {
    width: 100%;
    min-height: 5em;
    background-color: #444;
    box-shadow: 1px 1px 1px 3px rgba(4, 65, 34, 0.603);
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }

  input {
    min-width: 50%;
    margin: 0 1em;
    padding: 1em;
  }

  button {
    padding: 1.2em;
    margin: 0 0.2em;
    cursor: pointer;
    background-color: mediumseagreen;
    box-shadow: 1px 1px 3px 1px rgba(0, 0, 0, .5);
    border: 1px solid black;
    border-radius: 5px;
    color: white;
    font-weight: bold;
  }

  button:hover {
    background-color: rgb(78, 192, 129);
    transition: 0.2s all;
  }
</style>

<header>
  <input
    type="text"
    placeholder="Data"
    on:keydown={(e) => e.key === 'Enter' && apply()}
    bind:this={data} />
  <button id="apply" on:click={apply}>Apply</button>
  <button id="reset" on:click={reset}>Reset</button>
</header>

<Canvas data={code}/>

