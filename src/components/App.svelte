<script>
  let options = [""];
  let decision = "";

  function addOption() {
    options = [...options, ""];
  }

  function removeOption(index) {
    if (index === options.length - 1) {
      options = options.slice(0, index);
    } else {
      options = [...options.slice(0, index), ...options.slice(index + 1)];
    }
  }

  function chooseRandomOption() {
    const randomIndex = Math.floor(Math.random() * options.length);
    decision = options[randomIndex];
  }

  function clear() {
    options = [];
  }
</script>

<div class="app">
  <main class="container mx-auto px-5 mt-10">
    <div class="text-2xl mb-3">What are the options?</div>
    {#each options as option, i}
      <div class="my-2">
        <input
          type="text"
          bind:value={option}
          class="shadow border py-1 px-2 w-64" />
        <button
          on:click={() => removeOption(i)}
          class="button mx-1 rounded py-1 px-3 text-sm">
          ❌
        </button>
      </div>
    {/each}
    <div class="my-2">
      <button
        on:click={addOption}
        class="button rounded bg-gray-200 mt-2 mb-10 px-3 py-1">
        Add option
      </button>
    </div>
    <div class="my-2">
      <button
        on:click={chooseRandomOption}
        class="button rounded bg-blue-600 font-semibold text-lg text-white px-3
        py-2 w-full sm:w-1/4">
        Make Decision
      </button>
    </div>
    {#if decision}
      <div class="my-5">
        <div class="text-lg">The decision is...</div>
        <div class="text-2xl">{decision}</div>
      </div>
    {/if}
  </main>
</div>
