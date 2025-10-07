<script lang="ts" module>
  import { Button } from "$lib/registry/ui/button/index.js";
  import { cn } from "$lib/utils.js";
  import Icon from "@iconify/svelte";
  import type { HTMLAttributes } from "svelte/elements";

  type Social = {
    url: string;
    icon: string;
  };

  type Community1Props = {
    logo?: {
      src: string;
      alt: string;
      title: string;
      subtitle: string;
    };
    socials?: Social[];
  };
</script>

<script lang="ts">
  let {
    logo = {
      src: "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/logos/shadcnblockscom-icon.svg",
      alt: "logo",
      title: "Join our community",
      subtitle: "of designers & developers",
    },
    socials = [
      { url: "https://x.com/shadcnblocks", icon: "simple-icons:twitter" },
      { url: "https://github.com/shadcnblocks", icon: "simple-icons:github" },
      { url: "https://shadcnblocks.com", icon: "simple-icons:discord" },
    ],
    class: className,
    ...restProps
  }: Community1Props & HTMLAttributes<HTMLElement> = $props();
</script>

<section class={cn("py-32", className)} {...restProps}>
  <div class="container">
    <div class="flex flex-col items-center gap-5">
      <img src={logo.src} alt={logo.alt} class="size-10" />
      <h2 class="text-center text-3xl font-semibold">
        {logo.title}
        <br />
        <span class="text-muted-foreground/80">
          {logo.subtitle}
        </span>
      </h2>
      <div class="flex items-center gap-4">
        {#each socials as social}
          <Button size="icon" variant="outline" asChild>
            <a
              href={social.url}
              target="_blank"
              class="flex size-10 items-center justify-center"
            >
              <Icon icon={social.icon} class="size-4" />
            </a>
          </Button>
        {/each}
      </div>
    </div>
  </div>
</section>
