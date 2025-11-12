<script lang="ts" module>
  import { cn } from "$lib/utils.js";
  import type { HTMLAttributes } from "svelte/elements";

  export type Cta11Props = {
    heading?: string;
    description?: string;
    image?: { src: string; alt: string };
  };
</script>

<script lang="ts">
  let {
    heading = "Call to Action",
    description = "Build faster with our collection of pre-built blocks. Speed up your development and ship features in record time.",
    image = {
      src: "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/placeholder-dark-1.svg",
      alt: "Call to action image",
    },
    class: className,
    ...restProps
  }: Cta11Props & HTMLAttributes<HTMLElement> = $props();
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
      <div class="shrink-0">
        <div
          class="flex flex-col justify-center gap-4 sm:flex-row sm:items-center"
        >
          <div
            class="relative h-32 w-32 overflow-hidden rounded-lg sm:h-40 sm:w-40"
          >
            <img src={image.src} alt={image.alt} class="object-cover" />
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
