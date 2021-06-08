<script>
  import Theme from "./theme.svelte";
  import {
    MDBNavbar,
    MDBNavbarBrand,
    MDBNavbarNav,
    MDBNavItem,
    MDBNavLink,
    MDBNavbarToggler,
    MDBCollapse,
    MDBIcon,
  } from "mdbsvelte";

  let isOpen = false;

  function toggleCollapse() {
    isOpen = !isOpen;
  }

  function handleUpdate(event) {
    isOpen = event.detail.isOpen;
  }
</script>

<MDBNavbar color="black" dark expand="md">
  <MDBNavbarBrand>
    <strong class="white-text">Todo app with Svelete</strong>
  </MDBNavbarBrand>
  <MDBNavbarToggler on:click={toggleCollapse} />
  <MDBCollapse
    id="navbarCollapse3"
    {isOpen}
    navbar
    expand="md"
    on:update={handleUpdate}
  >
    <MDBNavbarNav left>
      <MDBNavItem active>
        <MDBNavLink to="#!">Home</MDBNavLink>
      </MDBNavItem>
    </MDBNavbarNav>
    <MDBNavbarNav right>
      <MDBNavItem>
        <MDBNavLink class="waves-effect waves-light" to="#!">
          <Theme>Toggle</Theme>
        </MDBNavLink>
      </MDBNavItem>
    </MDBNavbarNav>
  </MDBCollapse>
</MDBNavbar>

<style>
  :global(body) {
    background-color: #f2eee2;
    color: #0084f6;
    transition: background-color 0.3s;
  }
  :global(body.dark-mode) {
    background-color: #1d3040;
    color: #bfc2c7;
  }
</style>
