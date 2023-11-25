<script lang="ts">
  import Icon from "@iconify/svelte";
  import AngdButton from "../components/Buttons/AngdButton.svelte";
  import CosmoButton from "../components/Buttons/CosmoButton.svelte";
  import PopprButton from "../components/Buttons/PopprButton.svelte";
  import Container from "../components/Container.svelte";
</script>

<div class="min-h-screen bg-neutral-900 p-4 flex flex-col space-y-2">
  <Container>
    <CosmoButton>Join waitlist</CosmoButton>
    <PopprButton>Get in touch</PopprButton>
  </Container>
  <Container mode="light">
    <AngdButton>
      <svelte:fragment slot="icon">
        <Icon icon="ion:arrow-down-outline" class="text-white text-lg" />
      </svelte:fragment>
      Contact us
    </AngdButton>
  </Container>
</div>
