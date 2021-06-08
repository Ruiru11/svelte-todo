<script>
  import { MDBListGroupItem, MDBBtn, MDBIcon } from "mdbsvelte";
  import { createEventDispatcher, onMount } from "svelte";

  const dispatch = createEventDispatcher();

  let data = [];

  onMount(async () => {
    console.log("hiii");
    const res = await fetch(`https://api.quotable.io/random`);
    data = await res.json();
  });

  export let todoContent;
  export let todoItem
  let showItem = false;

  const toggleView = () => {
    showItem = !showItem;
  };

  const deletePlayer = () => {
    dispatch("removePlayer", name);
  };
</script>

<MDBListGroupItem color="light">
  <div class="d-flex w-100 justify-content-between">
    <h5 class="mb-1" style="font-size: large; font-weight: bold;">
      {todoItem} <MDBBtn size="sm" color="elegant" on:click={toggleView}
        >View</MDBBtn
      >
    </h5>
    <small>3 days ago</small>
  </div>
  {#if showItem}
    <p class="mb-1">
     {todoContent}
      <button class="btn">+1</button>
      <button class="btn btn-dark">-1</button>
    </p>
    <h6 style="color:green;font-style: italic;font-size: small;">
      {`"${data.content}"`}
    </h6>
  {/if}
</MDBListGroupItem>
