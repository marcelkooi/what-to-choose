<script>
  let options = [""];
  let decision = "";

  function addOption() {
    options = [...options, ""];
  }

  function chooseRandomOption() {
    const randomIndex = Math.floor(Math.random() * options.length);
    decision = options[randomIndex];
  }
</script>

<div class="app">
  <main class="container mx-auto mt-10">
    <div class="text-2xl mb-3">What are the options?</div>
    {#each options as option, i}
      <div class="my-2">
        <input
          type="text"
          bind:value={option}
          class="shadow border py-1 px-2 w-64" />
      </div>
    {/each}
    <div class="my-2">
      <button on:click={addOption} class="button rounded bg-gray-200 px-3 py-1">
        Add option
      </button>
    </div>
    <div class="my-2">
      <button
        on:click={chooseRandomOption}
        class="button rounded bg-blue-600 font-bold text-white px-3 py-1">
        Choose Option
      </button>
    </div>
    {#if decision}
      <div>The decision is...</div>
      <div>{decision}</div>
    {/if}
  </main>
</div>
