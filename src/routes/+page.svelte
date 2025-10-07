<script lang="ts">
  import Community1 from "$lib/registry/blocks/community1/community1.svelte";
  import Navbar1 from "$lib/registry/blocks/navbar1/navbar1.svelte";
  import Stats8 from "$lib/registry/blocks/stats8/stats8.svelte";
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

<main class="mx-auto flex max-w-5xl flex-col gap-8 pt-8 pb-16">
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

  <BlockDemo>
    {#snippet name()}
      Community1
    {/snippet}
    {#snippet description()}
      A component featuring a logo, a call-to-action for joining a community,
      and social buttons.
    {/snippet}
    <Community1 />
  </BlockDemo>

  <BlockDemo>
    {#snippet name()}
      Stats8
    {/snippet}
    {#snippet description()}
      A stats display component with a heading, description, and link, followed
      by a 4-column layout for statistics.
    {/snippet}
    <Stats8 />
  </BlockDemo>
</main>
