<script>
  import { users } from '../store';
  let userData;

  $: {
    userData = $users || [];
  }
</script>

{#if userData.length > 0}
  <ul>
    {#each userData as company}
      <li>
        <span><a href="/">{company.company.name}</a>, </span><span
          >{company.company.catchPhrase},
        </span><span>1</span>
      </li>
    {/each}
  </ul>
{:else}
  <p>Loading...</p>
{/if}
