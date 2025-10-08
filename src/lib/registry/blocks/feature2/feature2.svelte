<script lang="ts" module>
  import { Button } from "$lib/registry/ui/button/index.js";
  import { cn } from "$lib/utils.js";
  import type { HTMLAttributes } from "svelte/elements";

  type Feature2Props = {
    title?: string;
    description?: string;
    image?: { src: string; alt: string };
    buttons?: {
      primary?: {
        text: string;
        url: string;
      };
      secondary?: {
        text: string;
        url: string;
      };
    };
  };
</script>

<script lang="ts">
  let {
    title = "Blocks built with Shadcn & Tailwind",
    description = "Hundreds of finely crafted components built with React, Tailwind and Shadcn UI. Developers can copy and paste these blocks directly into their project.",
    image = {
      src: "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/placeholder-1.svg",
      alt: "Placeholder here",
    },
    buttons = {
      primary: {
        text: "Get Started",
        url: "https://shadcnblocks.com",
      },
      secondary: {
        text: "Learn More",
        url: "https://shadcnblocks.com",
      },
    },
    class: className,
    ...restProps
  }: Feature2Props & HTMLAttributes<HTMLElement> = $props();
</script>

<section class={cn("py-32", className)} {...restProps}>
  <div class="container">
    <div class="grid items-center gap-8 lg:grid-cols-2">
      <img
        src={image.src}
        alt={image.alt}
        class="max-h-96 w-full rounded-md object-cover"
      />
      <div
        class="flex flex-col items-center text-center lg:items-start lg:text-left"
      >
        <h1 class="my-6 mt-0 text-4xl font-semibold text-balance lg:text-5xl">
          {title}
        </h1>
        <p class="mb-8 max-w-xl text-muted-foreground lg:text-lg">
          {description}
        </p>
        <div
          class="flex w-full flex-col justify-center gap-2 sm:flex-row lg:justify-start"
        >
          {#if buttons.primary}
            <Button href={buttons.primary.url} target="_blank">
              {buttons.primary.text}
            </Button>
          {/if}
          {#if buttons.secondary}
            <Button
              variant="outline"
              href={buttons.secondary.url}
              target="_blank"
            >
              {buttons.secondary.text}
            </Button>
          {/if}
        </div>
      </div>
    </div>
  </div>
</section>
