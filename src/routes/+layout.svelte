<script>
  import '../app.css';
  import { onMount } from 'svelte';
  import { users } from '../store';

  onMount(async () => {
    try {
      const response = await fetch('https://jsonplaceholder.typicode.com/users');
      const data = await response.json();
      users.set(data);
    } catch (error) {
      console.error('Error fetching data:', error);
    }
  });
</script>

<slot />
