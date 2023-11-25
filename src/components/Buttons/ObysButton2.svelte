<script lang="ts">
  import { onMount } from "svelte";

  let button: HTMLButtonElement;
  let displayText: HTMLDivElement;
  let revealText: HTMLDivElement;

  const animationSpacing = 50;

  let fromPercentageDisplay = 0;
  let toPercentageDisplay = 0;
  let displayTextAnimationInterval: any = null;

  let revealTextAnimationInterval: any = null;
  let fromPercentageReveal = 0;
  let toPercentageReveal = 0;

  onMount(() => {
    button.onmouseenter = () => {
      fadeOutDisplayText();
      fadeInRevealText();
    };

    button.onmouseleave = () => {
      fadeInDisplayText();
      fadeOutRevealText();
    };
  });

  const fadeInRevealText = () => {
    if (revealTextAnimationInterval) clearInterval(revealTextAnimationInterval);

    revealTextAnimationInterval = setInterval(() => {
      if (fromPercentageReveal <= 99) {
        if (toPercentageReveal >= animationSpacing) {
          fromPercentageReveal += 1;
        }
      } else {
        fromPercentageReveal = 100;
        clearInterval(revealTextAnimationInterval);
      }
      if (toPercentageReveal <= 99) {
        toPercentageReveal += 1;
      } else {
        toPercentageReveal = 100;
      }

      console.log(fromPercentageReveal, toPercentageReveal);

      revealText.style.backgroundImage = `linear-gradient(to right, #fff ${fromPercentageReveal}%, transparent ${toPercentageReveal}%)`;
    }, 1);
  };

  const fadeOutRevealText = () => {
    if (revealTextAnimationInterval) clearInterval(revealTextAnimationInterval);

    revealTextAnimationInterval = setInterval(() => {
      if (fromPercentageReveal >= 1) {
        fromPercentageReveal -= 1;
      } else {
        fromPercentageReveal = 0;
      }

      if (toPercentageReveal >= 1) {
        if (fromPercentageReveal <= 100 - animationSpacing) {
          toPercentageReveal -= 1;
        }
      } else {
        toPercentageReveal = 0;
        clearInterval(revealTextAnimationInterval);
      }

      console.log(fromPercentageReveal, toPercentageReveal);

      revealText.style.backgroundImage = `linear-gradient(to right, #fff ${fromPercentageReveal}%, transparent ${toPercentageReveal}%)`;
    }, 1);
  };

  const fadeOutDisplayText = () => {
    if (displayTextAnimationInterval)
      clearInterval(displayTextAnimationInterval);

    displayTextAnimationInterval = setInterval(() => {
      if (fromPercentageDisplay <= 99) {
        if (toPercentageDisplay >= animationSpacing) {
          fromPercentageDisplay += 1;
        }
      } else {
        fromPercentageDisplay = 100;
        clearInterval(displayTextAnimationInterval);
      }
      if (toPercentageDisplay <= 99) {
        toPercentageDisplay += 1;
      } else {
        toPercentageDisplay = 100;
      }

      displayText.style.backgroundImage = `linear-gradient(to right, transparent ${fromPercentageDisplay}%, #fff ${toPercentageDisplay}%)`;
    }, 1);
  };

  const fadeInDisplayText = () => {
    if (displayTextAnimationInterval)
      clearInterval(displayTextAnimationInterval);

    displayTextAnimationInterval = setInterval(() => {
      if (fromPercentageDisplay >= 1) {
        fromPercentageDisplay -= 1;
      } else {
        fromPercentageDisplay = 0;
      }

      if (toPercentageDisplay >= 1) {
        if (fromPercentageDisplay <= 100 - animationSpacing) {
          toPercentageDisplay -= 1;
        }
      } else {
        toPercentageDisplay = 0;
        clearInterval(displayTextAnimationInterval);
      }

      displayText.style.backgroundImage = `linear-gradient(to right, transparent ${fromPercentageDisplay}%, #fff ${toPercentageDisplay}%)`;
    }, 1);
  };
</script>

<button
  bind:this={button}
  class="relative group {$$props.class} flex space-x-2 items-center"
  {...$$restProps}
>
  <div class="relative">
    <div
      bind:this={displayText}
      class="whitespace-nowrap font-['Onest'] font-bold text-3xl pointer-events-none w-full h-full top-0 left-0 bg-clip-text text-transparent bg-gradient-to-r from-transparent from-0% to-0% to-white"
    >
      <slot />
    </div>
    <div
      bind:this={revealText}
      class="absolute top-1/2 -translate-y-1/2 whitespace-nowrap font-['Londrina'] italic font-bold tracking-[0.155em] text-3xl bg-clip-text text-transparent bg-gradient-to-r from-white from-0% to-0% to-transparent"
    >
      <slot />
    </div>
  </div>
  <div class="group-hover:translate-x-1 transition-all ease-out duration-1000">
    <slot name="icon" />
  </div>
</button>

<style>
  .text-outline {
    color: transparent;
    -webkit-text-stroke: 1px #fff;
  }
</style>
