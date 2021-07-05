<script>
  import { MDBListGroupItem, MDBBtn, MDBIcon,MDBContainer, MDBModal, MDBModalBody, MDBModalHeader, MDBModalFooter } from "mdbsvelte";
  import { createEventDispatcher, onMount } from "svelte";

  const dispatch = createEventDispatcher();

  let data = [];
  let modal = false;
  let name = "";

  onMount(async () => {
    console.log("hiii");
    const res = await fetch(`https://api.quotable.io/random`);
    data = await res.json();
  });

  export let todoContent;
  export let todoItem
  let showItem = false;

  const onchange = (event) => {
    console.log("ecenf",event.target.value)
  }

  const toggleView = () => {
    showItem = !showItem;
  };

  const toggle = () => {
    modal=!modal
  }

  const deletePlayer = () => {
    dispatch("removePlayer", name);
  };
</script>

<MDBListGroupItem color="light">
  <input value={name} on:input={onchange}>
  <div class="d-flex w-100 justify-content-between">
    <MDBBtn color="primary" on:click={()=>toggle()}>Medium modal</MDBBtn>
  <MDBModal isOpen={modal} toggle={()=>toggle()}>
    <MDBModalHeader toggle={()=>toggle()}>MDBModal title</MDBModalHeader>
    <MDBModalBody>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore
      magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
      consequat.
    </MDBModalBody>
    <MDBModalFooter>
      <MDBBtn color="secondary" on:click={()=>toggle(2)}>Close</MDBBtn>
      <MDBBtn color="primary">Save changes</MDBBtn>
    </MDBModalFooter>
  </MDBModal>
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
