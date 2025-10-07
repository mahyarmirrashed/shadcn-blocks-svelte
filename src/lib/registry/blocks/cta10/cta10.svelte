<script lang="ts" module>
  import { Button } from "$lib/registry/ui/button/index.js";
  import { cn } from "$lib/utils.js";
  import type { HTMLAttributes } from "svelte/elements";

  type Cta10Props = {
    heading?: string;
    description?: string;
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
    heading = "Call to Action",
    description = "Build faster with our collection of pre-built blocks. Speed up your development and ship features in record time.",
    buttons = {
      primary: {
        text: "Buy Now",
        url: "https://www.shadcnblocks.com",
      },
    },
    class: className,
    ...restProps
  }: Cta10Props & HTMLAttributes<HTMLElement> = $props();
</script>

<section class={cn("py-32", className)} {...restProps}>
  <div class="container">
    <div
      class="flex w-full flex-col gap-16 overflow-hidden rounded-lg bg-accent p-8 md:rounded-xl lg:flex-row lg:items-center lg:p-12"
    >
      <div class="flex-1">
        <h3 class="mb-3 text-2xl font-semibold md:mb-4 md:text-4xl lg:mb-6">
          {heading}
        </h3>
        <p class="max-w-xl text-muted-foreground lg:text-lg">
          {description}
        </p>
      </div>
      <div class="flex shrink-0 flex-col gap-2 sm:flex-row">
        {#if buttons.secondary}
          <Button variant="outline" href={buttons.secondary.url}>
            {buttons.secondary.text}
          </Button>
        {/if}
        {#if buttons.primary}
          <Button variant="default" size="lg" href={buttons.primary.url}>
            {buttons.primary.text}
          </Button>
        {/if}
      </div>
    </div>
  </div>
</section>
