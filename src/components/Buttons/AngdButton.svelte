<script lang="ts">
  import { onMount } from "svelte";

  let iconContainer: HTMLDivElement;
  let textContainer: HTMLDivElement;

  onMount(() => {
    iconContainer.style.width = `${iconContainer.offsetHeight}px`;
    textContainer.style.paddingLeft = `calc(2rem + ${iconContainer.offsetHeight}px)`;
  });
</script>

<button
  class="flex relative border-[3px] border-neutral-700 rounded-full from-blue-100 to-orange-200 bg-gradient-to-b p-[3px] {$$props.class}"
  {...$$restProps}
>
  <div
    class="absolute from-blue-100 to-orange-200 bg-gradient-to-b top-0 left-0 rounded-full h-full aspect-square z-10"
  ></div>
  <div
    bind:this={iconContainer}
    class="absolute top-1/2 aspect-square -translate-y-1/2 rounded-full h-[calc(100%-6px)] bg-neutral-700 border-[3px] border-transparent z-20"
  >
    <div class="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2">
      <slot name="icon" />
    </div>
  </div>
  <div
    bind:this={textContainer}
    class="bg-neutral-700 rounded-full py-2 pr-8 pl-[72px] text-white font-['Syne'] whitespace-nowrap"
  >
    <slot />
  </div>
</button>
