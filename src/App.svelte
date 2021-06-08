<script>
  import { MDBContainer, MDBRow, MDBCol } from "mdbsvelte";

  import Navbar from "./navbar.svelte";
  import Todo from "./todo.svelte";
  import About from "./about.svelte";

  let players = [
    {
      name: "John Doe",
      points: 53,
    },
    {
      name: "Sam Smith",
      points: 45,
    },
    {
      name: "Sara Wilson",
      points: 34,
    },
  ];

  const addplayer = (e) => {
    console.log("eee", e.detail);
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };

  const removePlayer = (e) => {
    console.log("test", e.detail);
    players = players.filter((player) => player.name !== e.detail);
  };
  console.log(players);
</script>

<Navbar />
<MDBContainer>
  <About on:addplayer={addplayer} />
  {#if players.length === 0}
    <p>No players</p>
  {:else}
    {#each players as player}
      <Todo
        points={player.points}
        on:removePlayer={removePlayer}
      />
    {/each}
  {/if}
  <Todo />
</MDBContainer>
