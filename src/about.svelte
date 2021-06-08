<script>
  import {
    MDBJumbotron,
    MDBBtn,
    MDBContainer,
    MDBRow,
    MDBCol,
    MDBCardTitle,
    MDBIcon,
  } from "mdbsvelte";

  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let player = {
    name: "",
    points: 0,
  };

  const onSubmit = (e) => {
    e.preventDefault();
    dispatch("addplayer", player);
    player = {
      name: "",
      points: 0,
    };
  };
</script>

<MDBContainer>
  <MDBRow>
    <MDBCol>
      <MDBJumbotron style="padding: 0">
        <MDBCol
          class="text-white text-center "
          style="background-image: url(https://res.cloudinary.com/dxecwuaqd/image/upload/v1622505570/459659_bniow3.jpg)"
        >
          <MDBCol class="py-5">
            <MDBCardTitle class="h1-responsive pt-3 m-5 font-bold"
              >Never look back unless you are planning to go that way.
            </MDBCardTitle>
            <p class="mx-5 mb-5">
              Sometimes we forget that a plan is document that puts structure
              around an idea. But without that vision to set the plan in motion,
              there’s really no point in following through. Feminist icon Gloria
              Steinem understands that before there is a plan, there is a dream.
              That’s always the first step in any plan.
            </p>
          </MDBCol>
        </MDBCol>
      </MDBJumbotron>
    </MDBCol>
  </MDBRow>
</MDBContainer>
