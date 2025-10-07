<script lang="ts">
  import Navbar1 from "$lib/registry/blocks/navbar1/navbar1.svelte";
  import BlockDemo from "./block-demo.svelte";
</script>

<svelte:head>
  <title>ShadCN Blocks for Svelte</title>
</svelte:head>

<header class="mx-auto flex max-w-3xl flex-col gap-1 py-8">
  <h1 class="text-3xl font-bold tracking-tight">
    Registry for Svelte-based ShadCN Blocks
  </h1>
  <p class="text-muted-foreground">
    Svelte port of <a href="https://www.shadcnblocks.com" class="underline"
      >ShadCN Blocks</a
    >
    by
    <a href="https://github.com/mahyarmirrashed" class="underline"
      >Mahyar Mirrashed</a
    >, originally by
    <a href="https://twitter.com/ausrobdev" class="underline">Rob Austin</a>.
  </p>
</header>

<main class="mx-auto flex max-w-5xl flex-col gap-8">
  <BlockDemo>
    {#snippet name()}
      Navbar1
    {/snippet}
    {#snippet description()}
      A navigational component with dynamic menus, offering desktop and mobile
      layouts, incorporating icons and accordion features for sub-menus.
    {/snippet}

    <Navbar1 class="w-full" />
  </BlockDemo>
</main>
