<script>
  import {
    MDBNavbar,
    MDBNavbarBrand,
    MDBNavbarNav,
    MDBNavItem,
    MDBNavLink,
    MDBNavbarToggler,
    MDBCollapse,
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
  </MDBCollapse>
</MDBNavbar>
