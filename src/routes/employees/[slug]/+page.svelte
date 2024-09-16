<script>
  import { users } from '../../../store';
  import { browser } from '$app/environment';
  let currentCompany;

  if (browser) {
    currentCompany = window.location.pathname.replace('/employees/', '');
  }
</script>

<div class="mx-auto max-w-7xl">
  <div class="bg-gray-900 py-10">
    <div class="px-4 sm:px-6 lg:px-8">
      <div class="sm:flex sm:items-center">
        <div class="sm:flex-auto">
          <h1 class="text-base font-semibold leading-6 text-white">{currentCompany} Employees</h1>
          <p class="mt-2 text-sm text-gray-300">
            Please contact one of our sales representatives for more information.
          </p>
        </div>
      </div>
      <div class="mt-8 flow-root">
        <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
          <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
            {#each $users as user}
              <ul role="list" class="grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-3">
                {#if user.company.name.replaceAll(' ', '') === currentCompany}
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
                        <p class="mt-0.5 truncate text-sm text-gray-500">{user.email}</p>
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
