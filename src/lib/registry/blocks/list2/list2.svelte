<script lang="ts" module>
  import { Button } from "$lib/registry/ui/button/index.js";
  import { Separator } from "$lib/registry/ui/separator/index.js";
  import { cn } from "$lib/utils.js";
  import Icon from "@iconify/svelte";
  import type { HTMLAttributes } from "svelte/elements";

  type ListItem = {
    icon: string;
    title: string;
    category: string;
    description: string;
    link: string;
  };

  type List2Props = {
    heading?: string;
    items?: ListItem[];
  };
</script>

<script lang="ts">
  let {
    heading = "Our Achievements & Recognition",
    items = [
      {
        icon: "lucide:trophy",
        title: "Industry Recognition",
        category: "Achievement",
        description: "Outstanding Performance Award.",
        link: "#",
      },
      {
        icon: "lucide:award",
        title: "Excellence Award",
        category: "Recognition",
        description: "Best in Category Winner.",
        link: "#",
      },
      {
        icon: "lucide:lightbulb",
        title: "Innovation Prize",
        category: "Technology",
        description: "Breakthrough Solution of the Year.",
        link: "#",
      },
      {
        icon: "lucide:heart-handshake",
        title: "Customer Success",
        category: "Service",
        description: "Top-Rated Solution Provider.",
        link: "#",
      },
      {
        icon: "lucide:building-2",
        title: "Global Leadership",
        category: "Management",
        description: "Executive Team of the Year.",
        link: "#",
      },
      {
        icon: "lucide:leaf",
        title: "Sustainability Impact",
        category: "Environmental",
        description: "Green Initiative Excellence.",
        link: "#",
      },
    ],
    class: className,
    ...restProps
  }: List2Props & HTMLAttributes<HTMLElement> = $props();
</script>

<section class={cn("py-32", className)} {...restProps}>
  <div class="container px-0 md:px-8">
    <h1 class="mb-10 px-4 text-3xl font-semibold md:mb-14 md:text-4xl">
      {heading}
    </h1>
    <div class="flex flex-col">
      <Separator />
      {#each items as item}
        <div class="grid items-center gap-4 px-4 py-5 md:grid-cols-4">
          <div class="order-2 flex items-center gap-2 md:order-none">
            <span
              class="flex h-14 w-16 shrink-0 items-center justify-center rounded-md bg-muted"
            >
              <Icon icon={item.icon} class="size-6" />
            </span>
            <div class="flex flex-col gap-1">
              <h3 class="font-semibold">{item.title}</h3>
              <p class="text-sm text-muted-foreground">
                {item.category}
              </p>
            </div>
          </div>
          <p class="order-1 text-2xl font-semibold md:order-none md:col-span-2">
            {item.description}
          </p>
          <Button variant="outline" href={item.link} class="ml-auto">
            View project
            <Icon icon="lucide:arrow-right" class="size-4" />
          </Button>
        </div>
        <Separator />
      {/each}
    </div>
  </div>
</section>
