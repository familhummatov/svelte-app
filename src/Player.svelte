<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let name;
  export let points;
  export let index;
  let showControls = false;

  const increase = () => (points += 1);
  const decrease = () => (points -= 1);
  const toggle = () => (showControls = !showControls);
</script>

<div class="card">
  <h1 class="">
    {name}
    <button class="btn btn-sm" on:click={toggle}
      >{#if showControls}-{:else}+{/if}</button
    >
    <button
      class="btn btn-danger btn-sm"
      on:click={() => dispatch("delete", index)}>x</button
    >
  </h1>

  <h3>Points: {points}</h3>
  {#if showControls}
    <button class="btn" on:click={increase}>+1</button>
    <button class="btn btn-dark" on:click={decrease}>-1</button>
    <input type="number" bind:value={points} />
  {/if}
</div>

<style>
  h1 {
    color: #204f6e;
  }
  h3 {
    margin-bottom: 10px;
  }
</style>
