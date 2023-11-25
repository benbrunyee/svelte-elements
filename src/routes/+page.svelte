<script lang="ts">
  import Icon from "@iconify/svelte";
  import AngdButton from "../components/Buttons/AngdButton.svelte";
  import CosmoButton from "../components/Buttons/CosmoButton.svelte";
  import ObysButton from "../components/Buttons/ObysButton.svelte";
  import ObysButton2 from "../components/Buttons/ObysButton2.svelte";
  import PopprButton from "../components/Buttons/PopprButton.svelte";
  import Container from "../components/Container.svelte";
</script>

<div class="min-h-screen bg-neutral-900 p-4 flex flex-col space-y-2">
  <Container>
    <CosmoButton>Join waitlist</CosmoButton>
    <PopprButton>Get in touch</PopprButton>
    <ObysButton>
      <svelte:fragment slot="icon">
        <Icon icon="pajamas:long-arrow" class="text-white text-3xl" />
      </svelte:fragment>
      LET'S CREATE
    </ObysButton>
    <ObysButton2>
      <svelte:fragment slot="icon">
        <Icon icon="pajamas:long-arrow" class="text-white text-3xl" />
      </svelte:fragment>
      LET'S CREATE
    </ObysButton2>
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
