<script lang="ts">
  export let button: HTMLButtonElement;
  let topText: HTMLDivElement;
  let bottomText: HTMLDivElement;

  let animationRunning = false;

  $: if (button) {
    const curButtonOnMouseEnter = button.onmouseenter;

    button.onmouseenter = function (this: GlobalEventHandlers, e: MouseEvent) {
      curButtonOnMouseEnter && curButtonOnMouseEnter.bind(this)(e);

      if (animationRunning) return;
      animationRunning = true;

      // Use CSS animation name (by setting to empty quotes)
      topText.style.animationName = "";
      bottomText.style.animationName = "";
      // For the first hover
      topText.style.animationPlayState = "running";
      bottomText.style.animationPlayState = "running";

      setTimeout(() => {
        // Remove the CSS animation name to reset
        topText.style.animationName = "none";
        bottomText.style.animationName = "none";
        animationRunning = false;
      }, 400);
    };
  }
</script>

<div class="relative {$$props.class}">
  <div bind:this={topText} class="animate-text-top">
    <slot />
  </div>
  <div
    bind:this={bottomText}
    class="animate-text-bottom w-full absolute left-1/2 -translate-x-1/2 top-1/2 translate-y-[25%] opacity-0"
  >
    <slot />
  </div>
</div>

<style>
  .animate-text-top {
    animation-name: animate-text-top;
    animation-duration: 400ms;
    animation-timing-function: ease-out;
    animation-delay: 0ms;
    animation-play-state: paused;
  }

  .animate-text-bottom {
    animation-name: animate-text-bottom;
    animation-duration: 400ms;
    animation-timing-function: ease-out;
    animation-delay: 0ms;
    animation-play-state: paused;
  }

  @keyframes animate-text-top {
    0% {
      opacity: 100%;
      transform: translateY(0%);
    }
    100% {
      opacity: 0%;
      transform: translateY(-75%);
    }
  }

  @keyframes animate-text-bottom {
    0% {
      opacity: 0%;
      transform: translate(-50%, 25%);
    }
    100% {
      opacity: 100%;
      transform: translate(-50%, -50%);
    }
  }
</style>
