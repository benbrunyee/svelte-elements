<script lang="ts">
  import { onMount } from "svelte";
  import FadingUpText from "../lib/FadingUpText.svelte";

  let button: HTMLButtonElement;
  let circleBackgrounds: HTMLDivElement;

  onMount(() => {
    let animationRunning = false;

    button.onmouseenter = () => {
      if (animationRunning) return;
      animationRunning = true;

      for (let i = 0; i < circleBackgrounds.children.length; i++) {
        const circle = circleBackgrounds.children[i] as HTMLDivElement;
        // Use CSS animation name (by setting to empty quotes)
        circle.style.animationName = "";
        // For the first hover
        circle.style.animationPlayState = "running";
      }
      setTimeout(() => {
        for (let i = 0; i < circleBackgrounds.children.length; i++) {
          const circle = circleBackgrounds.children[i] as HTMLDivElement;
          // Remove the CSS animation name to reset
          circle.style.animationName = "none";
        }
        animationRunning = false;
      }, 800);
    };
  });
</script>

<button
  bind:this={button}
  class="relative rounded-full overflow-hidden py-3 px-8 font-['Syne'] font-bold transition-all duration-[400ms] group hover:scale-x-[98%] ease-out {$$props.class}"
  {...$$restProps}
>
  <FadingUpText {button} class="z-[1]"><slot /></FadingUpText>
  <div
    class="absolute w-full h-full bg-[#FFD075] py-3 px-8 left-1/2 -translate-x-1/2 top-1/2 -translate-y-1/2"
  ></div>

  <div bind:this={circleBackgrounds}>
    <div
      class="circle-animation-1 w-[200%] absolute bg-purple-400 aspect-square rounded-full left-1/2 top-full"
    ></div>
    <div
      class="circle-animation-2 w-[200%] absolute bg-teal-300 aspect-square rounded-full left-1/2 top-full"
    ></div>
    <div
      class="circle-animation-3 w-[200%] absolute bg-[#FFD075] aspect-square rounded-full left-1/2 top-full"
    ></div>
  </div>
</button>

<style>
  .circle-animation-1 {
    animation-name: circle-animate;
    animation-duration: 400ms;
    animation-timing-function: ease-out;
    animation-delay: 0ms;
    animation-fill-mode: backwards;
    animation-play-state: paused;
  }

  .circle-animation-2 {
    animation-name: circle-animate;
    animation-duration: 400ms;
    animation-timing-function: ease-out;
    animation-delay: 200ms;
    animation-fill-mode: backwards;
    animation-play-state: paused;
  }

  .circle-animation-3 {
    animation-name: circle-animate;
    animation-duration: 400ms;
    animation-timing-function: ease-out;
    animation-delay: 400ms;
    animation-fill-mode: backwards;
    animation-play-state: paused;
  }

  @keyframes circle-animate {
    0% {
      transform: translate(-50%, -25%) scale(50%);
    }
    100% {
      transform: translate(-50%, -25%) scale(100%);
    }
  }
</style>
