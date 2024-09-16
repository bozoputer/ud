<script>
  import { users } from '../../../store';
  import { browser } from '$app/environment';
  let currentCompany;

  if (browser) {
    currentCompany = window.location.pathname.replace('/employees/', '');
  }
</script>

<h1>Employees</h1>
{#each $users as user}
  <ul>
    {#if user.company.name.replaceAll(' ', '') === currentCompany}
      <p>{user.name}</p>
      <p>{user.address.street}</p>
      <p>{user.address.suite}</p>
      <p>{user.address.city}</p>
      <p>{user.address.zipcode}</p>
      <p>{user.phone}</p>
      <p>{user.email}</p>
    {/if}
  </ul>
{/each}
