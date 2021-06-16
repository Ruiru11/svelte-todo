<script>
  import { MDBContainer, MDBRow, MDBCol } from "mdbsvelte";
  import { onMount } from "svelte";

  import Navbar from "./navbar.svelte";
  import Todo from "./todo.svelte";
  import About from "./about.svelte";

  let Todos = [];

  onMount(async () => {
    console.log("hiii");
    const res = await fetch(
      `https://jsonplaceholder.typicode.com/posts?_todo=1&_limit=5`
    );
	console.log("get ", await res);
    Todos = await res.json();

    console.log("get ", Todos);
  });

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
  {#if Todos.length === 0}
    <p>No players</p>
  {:else}
    {#each Todos as todo}
      <Todo todoItem={todo.title} todoContent={todo.body} on:removePlayer={removePlayer} />
    {/each}
  {/if}
  <Todo />
</MDBContainer>
