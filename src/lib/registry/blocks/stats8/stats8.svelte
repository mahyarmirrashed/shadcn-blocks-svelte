<script lang="ts" module>
  import { cn } from "$lib/utils.js";
  import Icon from "@iconify/svelte";
  import type { HTMLAttributes } from "svelte/elements";

  type Stats8Props = {
    heading?: string;
    description?: string;
    link?: {
      text: string;
      url: string;
    };
    stats?: Array<{
      id: string;
      value: string;
      label: string;
    }>;
  };
</script>

<script lang="ts">
  let {
    heading = "Platform performance insights",
    description = "Ensuring stability and scalability for all users",
    link = {
      text: "Read the full impact report",
      url: "#",
    },
    stats = [
      {
        id: "stat-1",
        value: "250%+",
        label: "average growth in user engagement",
      },
      {
        id: "stat-2",
        value: "$2.5m",
        label: "annual savings per enterprise partner",
      },
      {
        id: "stat-3",
        value: "200+",
        label: "integrations with top industry platforms",
      },
      {
        id: "stat-4",
        value: "99.9%",
        label: "customer satisfaction over the last year",
      },
    ],
    class: className,
    ...restProps
  }: Stats8Props & HTMLAttributes<HTMLElement> = $props();
</script>

<section class={cn("py-32", className)} {...restProps}>
  <div class="container">
    <div class="flex flex-col gap-4">
      <h2 class="text-2xl font-bold md:text-4xl">{heading}</h2>
      <p>{description}</p>
      <a
        href={link.url}
        class="flex items-center gap-1 font-bold hover:underline"
      >
        {link.text}
        <Icon icon="lucide:arrow-right" class="h-auto w-4" />
      </a>
    </div>
    <div class="mt-14 grid gap-x-5 gap-y-8 md:grid-cols-2 lg:grid-cols-4">
      {#each stats as stat (stat.id)}
        <div class="flex flex-col gap-5">
          <div class="text-6xl font-bold">{stat.value}</div>
          <p>{stat.label}</p>
        </div>
      {/each}
    </div>
  </div>
</section>
