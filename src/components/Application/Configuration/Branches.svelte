<script>
  export let loading, branches;
  import { application } from "@store";
</script>

{#if loading}
  <div class="grid grid-cols-1">
    <label for="branch">Branch</label>
    <select disabled>
      <option selected>Loading branches</option>
    </select>
  </div>
{:else}
  <div class="grid grid-cols-1">
    <label for="branch">Branch</label>
    <!-- svelte-ignore a11y-no-onchange -->
    <select id="branch" bind:value="{$application.repository.branch}">
      <option disabled selected>Select a branch</option>
      {#each branches as branch}
        <option value="{branch.name}" class="font-medium">{branch.name}</option>
      {/each}
    </select>
  </div>
{/if}
