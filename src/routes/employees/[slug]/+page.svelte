<script>
  import { users } from '../../../store';
  import { browser } from '$app/environment';
  let currentCompany;
  let userData;
  let selected;

  $: {
    userData = $users || [];
  }

  if (browser) {
    currentCompany = window.location.pathname.replace('/employees/', '').replaceAll('%20', ' ');
  }

  function handleTransferEmployee() {
    alert(selected);
  }
</script>

<svelte:head>
  <title>{currentCompany} | Employees</title>
</svelte:head>;

<div class="mx-auto max-w-7xl">
  <div class="bg-gray-900 py-10">
    <div class="px-4 sm:px-6 lg:px-8">
      <div class="sm:flex sm:items-center">
        <div class="sm:flex-auto">
          <h1 class="text-base font-semibold leading-6 text-white">{currentCompany} Employees</h1>
        </div>
      </div>
      <div class="mt-8 flow-root">
        <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
          <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
            {#each $users as user (user.id)}
              <ul role="list" class="grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-3">
                {#if user.company.name.replaceAll('%20', ' ') === currentCompany}
                  <li class="col-span-1 divide-y divide-gray-200 rounded-lg bg-white shadow">
                    <div class="flex w-full items-center justify-between space-x-6 p-6">
                      <div class="flex-1 truncate">
                        <div class="flex items-center space-x-3">
                          <h3 class="truncate text-sm font-medium text-gray-900">{user.name}</h3>
                        </div>
                        <p class="mt-0.5 truncate text-sm text-gray-500">{user.address.street}</p>
                        <p class="mt-0.5 truncate text-sm text-gray-500">{user.address.suite}</p>
                        <p class="mt-0.5 truncate text-sm text-gray-500">
                          {user.address.city}, {user.address.zipcode}
                        </p>
                        <p class="mt-0.5 truncate text-sm text-gray-500">{user.phone}</p>
                        <p class="mt-0.5 mb-4 truncate text-sm text-gray-500">{user.email}</p>
                        <hr />
                        <label
                          for="location"
                          class="block text-xs mt-2 font-medium leading-6 text-gray-900"
                          >Transfer employee to:</label
                        >
                        <select
                          id="company"
                          name="company"
                          bind:value={selected}
                          on:change={handleTransferEmployee}
                          class="block w-56 rounded-md border-0 py-1 pl-3 pr-10 text-gray-900 ring-1 ring-inset ring-gray-300 focus:ring-2 focus:ring-indigo-600 text-xs sm:leading-6"
                        >
                          <option hidden disabled selected value>Select company </option>
                          {#each userData as company}
                            <option>{company.company.name}</option>
                          {/each}
                        </select>
                      </div>
                    </div>
                  </li>
                {/if}
              </ul>
            {/each}
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
