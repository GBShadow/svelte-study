<script lang="ts">
  import { createEventDispatcher } from "svelte";

  type Player = {
    name: string;
    points: number;
  }
  
  export let player: Player;

  const dispatch = createEventDispatcher()

  const addPoints = () => player.points += 1;
  const removePoints = () => player.points -= 1;

  const removePlayer = () => dispatch('removePlayer', player.name);
</script>

<div class="border border-white p-8 flex space-x-5 text-white">
  <div>
    <h1>{player.name}</h1>
    <h3>Points: {player.points}</h3>
  </div>
  <div class="flex flex-col align-center space-y-2">
    <button on:click={addPoints}  class="w-5 h-5 bg-blue-600" >+</button>
    <button on:click={removePoints}  class="w-5 h-5 bg-blue-600" >-</button>
  </div>
  <div class="flex align-center">
    <button on:click={removePlayer} class="w-10 bg-red-600">x</button>
  </div>
</div>