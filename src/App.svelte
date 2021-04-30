<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    { name: "Darth Maul", points: 89 },
    { name: "Luke Skywalker", points: 99 },
    { name: "Darth Vader", points: 96 },
    { name: "Obi Van Kenobi", points: 91 },
  ];

  const addPlayer = (e) => {
    players = [...players, e.detail];
  };

  const deletePlayer = (e) => {
    players.splice(e.detail, 1);
    players = [...players];
  };
</script>

<main class="container">
  <Navbar />
  <AddPlayer on:addplayer={addPlayer} />

  {#each players as player, i}
    <Player
      on:delete={deletePlayer}
      index={i}
      name={player.name}
      points={player.points}
    />
  {:else}
    <h3>No players</h3>
  {/each}
</main>
