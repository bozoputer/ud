<script>
  import { users } from '../store';
  let userData;

  $: {
    userData = $users || [];
  }
</script>

<svelte:head>
  <title>Acme Brands | Companies</title>
</svelte:head>

{#if userData.length > 0}
  <div class="bg-gray-900">
    <div class="mx-auto max-w-7xl">
      <div class="bg-gray-900 py-10">
        <div class="px-4 sm:px-6 lg:px-8">
          <div class="sm:flex sm:items-center">
            <div class="sm:flex-auto">
              <h1 class="text-base font-semibold leading-6 text-white">Acme Brands</h1>
              <p class="mt-2 text-sm text-gray-300">
                Companies under the Acme Brands corporate umbrella. Click a company name to navigate
                to the employee page.
              </p>
            </div>
          </div>
          <div class="mt-8 flow-root">
            <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
              <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
                <table class="min-w-full divide-y divide-gray-700">
                  <thead>
                    <tr>
                      <th
                        scope="col"
                        class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-white sm:pl-0"
                        >Company</th
                      >
                      <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-white"
                        >Catch Phrase</th
                      >
                      <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-white"
                        ># Employees</th
                      >
                    </tr>
                  </thead>
                  <tbody class="divide-y divide-gray-800">
                    {#each userData as company}
                      <tr>
                        <td
                          class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-white sm:pl-0"
                          ><a class="underline" href="employees/{company.company.name}"
                            >{company.company.name}</a
                          ></td
                        >
                        <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-300"
                          >{company.company.catchPhrase}</td
                        >
                        <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-300">1</td>
                        <td
                          class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-0"
                        >
                        </td>
                      </tr>
                    {/each}
                  </tbody>
                </table>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
{:else}
  <p>Loading...</p>
{/if}
