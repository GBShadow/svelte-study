<script lang="ts">
  import AddPlayer from './components/AddPlayer.svelte';
  import Navbar from './components/Navbar.svelte';
	import Player from './components/Player.svelte'

  type Player = {
    name: string;
    points: number;
  }

  let players: Player[] = [
    {
      name: 'GBS',
      points: 100,
    },
    {
      name: 'Pedro',
      points: 100,
    },
    {
      name: 'Feeh',
      points: 100,
    },
  ]

  const addPlayer = (e) => {
    const newPlayer = e.detail
    players = [...players, newPlayer]
  }

  const removePlayer = (e) => {
    players = players.filter(player => player.name !== e.detail)
  }
</script>

<Navbar /> 
<div class="p-8 max-w-6xl mx-auto bg-gray-500">
  <AddPlayer on:addPlayer={addPlayer} />

  {#if players.length === 0}
    <p>No players</p>
  {:else}
    {#each players as player}
      <Player on:removePlayer={removePlayer}  player={player} />
    {/each}
  {/if}

</div>

<style global lang="postcss">
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
</style>
