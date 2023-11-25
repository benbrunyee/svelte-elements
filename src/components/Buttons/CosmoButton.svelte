<script>
  import SlidingHoverText from "../lib/SlidingHoverText.svelte";
</script>

<button
  class="rounded-[14px] bg-white font-['Space_Grotesk'] py-2 px-6 font-bold relative z-[1] group {$$props.class}"
  {...$$restProps}
>
  <div
    class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 -z-[1] w-full h-full"
  >
    <div
      class="pointer-events-none w-2/3 absolute top-1/2 left-1/3 -translate-x-1/2 shadow-[0px_0px_50px_10px] opacity-60 shadow-red-300 rounded-full group-hover:opacity-90 transition-opacity duration-300 ease-in-out"
    ></div>
    <div
      class="pointer-events-none w-2/3 absolute top-1/2 left-2/3 -translate-x-1/2 shadow-[0px_0px_50px_10px] opacity-60 shadow-blue-300 rounded-full group-hover:opacity-90 transition-opacity duration-300 ease-in-out"
    ></div>
  </div>
  <SlidingHoverText>
    <slot />
  </SlidingHoverText>
</button>
