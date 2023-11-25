<script lang="ts">
  export let mode = "dark";
</script>

<div
  class="rounded-xl w-full {mode === 'dark'
    ? 'bg-neutral-800'
    : 'bg-neutral-200'} shadow-lg p-4 space-x-4 flex flex-wrap"
>
  <slot />
</div>
