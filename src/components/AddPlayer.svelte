<script lang="ts">
  import { createEventDispatcher } from 'svelte'

  const dispatch = createEventDispatcher()

  let player = {
    name: '',
    points: null
  }

  const onSubmit = (e) => {
    e.preventDefault();
    dispatch('addPlayer', player);
    
    player = {
    name: '',
    points: null
  }
  }
</script>


<form on:submit={onSubmit} class="flex flex-col space-y-4 px-10 mb-4">
  <input class="p-2" type="text" placeholder="Player Name" bind:value={player.name}>
  <input class="p-2" type="number" placeholder="Player Points" bind:value={player.points}>
  <input type="submit" value="Add player" class="py-2 px-4 bg-green-600 text-white cursor-pointer">
</form>