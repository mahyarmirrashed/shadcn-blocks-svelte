<script lang="ts">
  import Community1 from "$lib/registry/blocks/community1/community1.svelte";
  import Contact7 from "$lib/registry/blocks/contact7/contact7.svelte";
  import Navbar1 from "$lib/registry/blocks/navbar1/navbar1.svelte";
  import Stats8 from "$lib/registry/blocks/stats8/stats8.svelte";
  import BlockDemo from "./block-demo.svelte";
</script>

<svelte:head>
  <title>ShadCN Blocks, for Svelte</title>
</svelte:head>

{#snippet link(href: string, label: string)}
  <a {href} class="group underline hover:no-underline">
    <span
      class="bg-gradient-to-r from-muted-foreground to-muted-foreground bg-[length:0%_1px] bg-left-bottom bg-no-repeat transition-all duration-500 ease-out group-hover:bg-[length:100%_1px]"
    >
      {label}
    </span>
  </a>
{/snippet}

<header class="mx-auto flex max-w-3xl flex-col gap-1 py-8">
  <h1 class="text-3xl font-bold tracking-tight">ShadCN Blocks, for Svelte</h1>
  <p class="text-muted-foreground">
    Svelte port of {@render link(
      "https://www.shadcnblocks.com",
      "shadcnblocks.com",
    )} by {@render link(
      "https://github.com/mahyarmirrashed",
      "Mahyar Mirrashed",
    )}, originally by {@render link(
      "https://twitter.com/ausrobdev",
      "Rob Austin",
    )}
  </p>
</header>

<main class="mx-auto flex max-w-5xl flex-col gap-8 pt-8 pb-16">
  <BlockDemo name="community1">
    {#snippet description()}
      A component featuring a logo, a call-to-action for joining a community,
      and social buttons.
    {/snippet}
    <Community1 />
  </BlockDemo>

  <BlockDemo name="contact7">
    {#snippet description()}
      A contact block with title, description, and 3 columns for email, address,
      and phone, each with icons.
    {/snippet}
    <Contact7 />
  </BlockDemo>

  <BlockDemo name="navbar1">
    {#snippet description()}
      A navigational component with dynamic menus, offering desktop and mobile
      layouts, incorporating icons and accordion features for sub-menus.
    {/snippet}
    <Navbar1 class="w-full" />
  </BlockDemo>

  <BlockDemo name="stats8">
    {#snippet description()}
      A stats display component with a heading, description, and link, followed
      by a 4-column layout for statistics.
    {/snippet}
    <Stats8 />
  </BlockDemo>
</main>
