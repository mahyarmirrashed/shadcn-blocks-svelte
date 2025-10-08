<script lang="ts" module>
  import { cn } from "$lib/utils.js";
  import type { HTMLAttributes } from "svelte/elements";

  type Feature = {
    id: string;
    title: string;
    subtitle: string;
    description: string;
    image: string;
  };

  type Feature13Props = {
    heading?: string;
    features?: Feature[];
  };
</script>

<script lang="ts">
  let {
    heading = "A better way to build websites",
    features = [
      {
        id: "feature-1",
        title: "Built for artists and designers",
        subtitle: "FOR DESIGNERS",
        description:
          "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Minima doloribus illum, labore quis facilis molestias!",
        image:
          "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/placeholder-1.svg",
      },
      {
        id: "feature-2",
        title: "Built for coders and developers",
        subtitle: "FOR DEVELOPERS",
        description:
          "Lorem ipsum dolor sit, amet consectetur adipisicing elit. Minima doloribus illum, labore quis facilis molestias!",
        image:
          "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/placeholder-4.svg",
      },
    ],
    class: className,
    ...restProps
  }: Feature13Props & HTMLAttributes<HTMLElement> = $props();
</script>

<section class={cn("py-32", className)} {...restProps}>
  <div class="container max-w-7xl">
    <h2 class="text-3xl font-medium lg:text-4xl">{heading}</h2>
    <div class="mt-20 grid gap-9 lg:grid-cols-2">
      {#each features as feature}
        <div class="flex flex-col justify-between rounded-lg bg-accent">
          <div class="flex justify-between gap-10 border-b">
            <div
              class="flex flex-col justify-between gap-14 py-6 pl-4 md:py-10 md:pl-8 lg:justify-normal"
            >
              <p class="text-xs text-muted-foreground">
                {feature.subtitle}
              </p>
              <h3 class="text-2xl md:text-4xl">{feature.title}</h3>
            </div>
            <div class="md:1/3 w-2/5 shrink-0 rounded-r-lg border-l">
              <img
                src={feature.image}
                alt={feature.title}
                class="h-full w-full object-cover"
              />
            </div>
          </div>
          <div class="p-4 text-muted-foreground md:p-8">
            {feature.description}
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>
