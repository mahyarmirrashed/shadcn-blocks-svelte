<script lang="ts">
  import Community1 from "$lib/registry/blocks/community1/community1.svelte";
  import Contact7 from "$lib/registry/blocks/contact7/contact7.svelte";
  import Cta10 from "$lib/registry/blocks/cta10/cta10.svelte";
  import Cta11 from "$lib/registry/blocks/cta11/cta11.svelte";
  import Faq1 from "$lib/registry/blocks/faq1/faq1.svelte";
  import Feature1 from "$lib/registry/blocks/feature1/feature1.svelte";
  import Feature2 from "$lib/registry/blocks/feature2/feature2.svelte";
  import Feature13 from "$lib/registry/blocks/feature13/feature13.svelte";
  import Feature43 from "$lib/registry/blocks/feature43/feature43.svelte";
  import List2 from "$lib/registry/blocks/list2/list2.svelte";
  import Navbar1 from "$lib/registry/blocks/navbar1/navbar1.svelte";
  import Pricing6 from "$lib/registry/blocks/pricing6/pricing6.svelte";
  import Stats8 from "$lib/registry/blocks/stats8/stats8.svelte";
  import Team1 from "$lib/registry/blocks/team1/team1.svelte";
  import Testimonial10 from "$lib/registry/blocks/testimonial10/testimonial10.svelte";
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

<header class="mx-auto flex max-w-3xl flex-col gap-1 py-12">
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
    <Community1 class="py-16" />
  </BlockDemo>

  <BlockDemo name="contact7">
    {#snippet description()}
      A contact block with title, description, and 3 columns for email, address,
      and phone, each with icons.
    {/snippet}
    <Contact7 class="py-16" />
  </BlockDemo>

  <BlockDemo name="cta10">
    {#snippet description()}
      A call-to-action component with a heading, description, and optional
      primary and secondary buttons arranged in a single column that becomes a
      row on larger screens.
    {/snippet}
    <Cta10 class="py-16" />
  </BlockDemo>

  <BlockDemo name="cta11">
    {#snippet description()}
      A component with heading, description, and up to two buttons, arranged
      vertically with emphasis styling.
    {/snippet}
    <Cta11 class="py-16" />
  </BlockDemo>

  <BlockDemo name="faq1">
    {#snippet description()}
      An accordion-style FAQ component with a customizable heading and list of
      questions and answers.
    {/snippet}
    <Faq1 class="w-full py-16" />
  </BlockDemo>

  <BlockDemo name="feature1">
    {#snippet description()}
      A block with a 2-column layout featuring a title, description, two
      buttons, and an image.
    {/snippet}
    <Feature1 class="py-16" />
  </BlockDemo>

  <BlockDemo name="feature2">
    {#snippet description()}
      A block with a 2-column layout featuring a title, description, two
      buttons, and an image on the left.
    {/snippet}
    <Feature2 class="py-16" />
  </BlockDemo>

  <BlockDemo name="feature13">
    {#snippet description()}
      A component showcases a heading and 2-column layout of features with
      title, subtitle, description, and image. Unique for using images as visual
      endpoints in each feature card.
    {/snippet}
    <Feature13 class="py-16" />
  </BlockDemo>

  <BlockDemo name="feature43">
    {#snippet description()}
      A component showcasing 6 reasons with icons, titles, and descriptions in a
      3-column grid for "Why Work With Us?".
    {/snippet}
    <Feature43 class="py-16" />
  </BlockDemo>

  <BlockDemo name="list2">
    {#snippet description()}
      A component displaying a list of awards with icons, titles, categories,
      and descriptions. Includes headings and buttons to view details.
    {/snippet}
    <List2 class="py-16" />
  </BlockDemo>

  <BlockDemo name="navbar1">
    {#snippet description()}
      A navigational component with dynamic menus, offering desktop and mobile
      layouts, incorporating icons and accordion features for sub-menus.
    {/snippet}
    <Navbar1 class="w-full" />
  </BlockDemo>

  <BlockDemo name="pricing6">
    {#snippet description()}
      A pricing component with a heading, description, price, features list, and
      a call-to-action button. Features 3 groups of listed perks.
    {/snippet}
    <Pricing6 class="py-16" />
  </BlockDemo>

  <BlockDemo name="stats8">
    {#snippet description()}
      A stats display component with a heading, description, and link, followed
      by a 4-column layout for statistics.
    {/snippet}
    <Stats8 class="py-16" />
  </BlockDemo>

  <BlockDemo name="team1">
    {#snippet description()}
      A team showcase component with a title, subtitle, description, and a grid
      of member avatars, names, and roles, supporting up to 4 columns.
    {/snippet}
    <Team1 class="py-16" />
  </BlockDemo>

  <BlockDemo name="testimonial10">
    {#snippet description()}
      A testimonial block with a central quote, author's name, role, and avatar
      in a vertical layout.
    {/snippet}
    <Testimonial10 class="py-16" />
  </BlockDemo>
</main>
