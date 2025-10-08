<script lang="ts" module>
  import { cn } from "$lib/utils.js";
  import Icon from "@iconify/svelte";
  import type { HTMLAttributes } from "svelte/elements";

  type Service = {
    title: string;
    description: string;
    items: string[];
    icon: string;
  };

  type Services4Props = { services?: Service[] };
</script>

<script lang="ts">
  let {
    services = [
      {
        title: "Product Strategy",
        description:
          "Strategic planning and market positioning to ensure your product meets user needs and business goals.",
        items: ["Market Research", "User Personas", "Competitive Analysis"],
        icon: "lucide:cog",
      },
      {
        title: "Design",
        description:
          "Beautiful, user-centered designs that create engaging experiences across all platforms.",
        items: ["UI/UX Design", "Prototyping", "Interaction Design"],
        icon: "lucide:pen-tool",
      },
      {
        title: "Web Development",
        description:
          "Modern, scalable web applications built with the latest technologies and best practices.",
        items: ["Frontend Dev", "Backend Dev", "API Integration"],
        icon: "lucide:code",
      },
      {
        title: "Marketing",
        description:
          "Data-driven strategies to launch successfully and scale your product efficiently.",
        items: ["SEO Strategy", "Analytics & Data", "A/B Testing"],
        icon: "lucide:shrub",
      },
    ],
    class: className,
    ...restProps
  }: Services4Props & HTMLAttributes<HTMLElement> = $props();
</script>

<section class={cn("py-32", className)} {...restProps}>
  <div class="container">
    <div class="mx-auto max-w-6xl space-y-12">
      <div class="space-y-4 text-center">
        <h2 class="text-3xl font-semibold tracking-tight md:text-4xl">
          Services
        </h2>
        <p
          class="mx-auto max-w-2xl text-lg tracking-tight text-muted-foreground md:text-xl"
        >
          We craft digital experiences that captivate and convert, bringing your
          vision to life.
        </p>
      </div>

      <div class="grid grid-cols-1 gap-8 md:grid-cols-2">
        {#each services as service}
          <div
            class="space-y-6 rounded-lg border border-border p-8 transition-shadow hover:shadow-sm"
          >
            <div class="flex items-center gap-4">
              <div class="rounded-full bg-muted p-3">
                <Icon icon={service.icon} class="size-6" />
              </div>
              <h3 class="text-xl font-semibold">{service.title}</h3>
            </div>
            <p class="leading-relaxed text-muted-foreground">
              {service.description}
            </p>
            <div class="space-y-2">
              {#each service.items as item}
                <div class="flex items-center gap-2">
                  <div class="h-1.5 w-1.5 rounded-full bg-foreground"></div>
                  <span class="text-sm font-medium">{item}</span>
                </div>
              {/each}
            </div>
          </div>
        {/each}
      </div>
    </div>
  </div>
</section>
