<script lang="ts" module>
  import { Button } from "$lib/registry/ui/button/index.js";
  import { Separator } from "$lib/registry/ui/separator/index.js";
  import { cn } from "$lib/utils.js";
  import Icon from "@iconify/svelte";
  import type { HTMLAttributes } from "svelte/elements";

  export type Pricing6Props = {
    heading?: string;
    description?: string;
    price?: string | number;
    priceSuffix?: string;
    features?: string[][];
    buttonText?: string;
  };

  const defaultFeatures = [
    ["Unlimited", "Integrations", "24/7 support"],
    ["Live collaborations", "Unlimited storage", "30-day money back"],
    ["Unlimited members", "Customization", "Unlimited users"],
  ];
</script>

<script lang="ts">
  let {
    heading = "Pricing",
    description = "Simple pricing with a free 7 day trial.",
    price = 29,
    priceSuffix = "/mo",
    features = defaultFeatures,
    buttonText = "Start free trial",
    class: className,
    ...restProps
  }: Pricing6Props & HTMLAttributes<HTMLElement> = $props();
</script>

<section class={cn("py-32", className)} {...restProps}>
  <div class="container">
    <div class="mx-auto flex max-w-5xl flex-col items-center gap-6 text-center">
      <h2 class="text-4xl font-semibold text-pretty lg:text-6xl">
        {heading}
      </h2>
      <p class="max-w-md text-muted-foreground lg:text-xl">
        {description}
      </p>
      <div
        class="mx-auto flex w-full flex-col rounded-lg border p-6 sm:w-fit sm:min-w-80"
      >
        <div class="flex justify-center">
          <span class="text-lg font-semibold">$</span>
          <span class="text-6xl font-semibold">{price}</span>
          <span class="self-end text-muted-foreground">
            {priceSuffix}
          </span>
        </div>
        <div class="my-6">
          {#each features as featureGroup, idx}
            <ul class="flex flex-col gap-3">
              {#each featureGroup as feature}
                <li
                  class="flex items-center justify-between gap-2 text-sm font-medium"
                >
                  {feature}
                  <Icon icon="lucide:check" class="inline size-4 shrink-0" />
                </li>
              {/each}
            </ul>
            {#if idx < features.length - 1}
              <Separator class="my-6" />
            {/if}
          {/each}
        </div>
        <Button>{buttonText}</Button>
      </div>
    </div>
  </div>
</section>
