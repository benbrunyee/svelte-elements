<div class="overflow-clip relative {$$props.class}">
  <div
    class="group-hover:-translate-y-full transition-transform duration-500 ease-in-out"
  >
    <slot />
  </div>
  <div
    class="pointer-events-none absolute left-1/2 top-1/2 -translate-x-1/2 group-hover:-translate-y-1/2 translate-y-[50%] w-full transition-transform duration-500 ease-in-out"
  >
    <slot />
  </div>
</div>
