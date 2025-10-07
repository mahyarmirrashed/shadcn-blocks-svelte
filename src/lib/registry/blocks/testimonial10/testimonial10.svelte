<script lang="ts" module>
  import * as Avatar from "$lib/registry/ui/avatar/index.js";
  import { cn } from "$lib/utils.js";
  import type { HTMLAttributes } from "svelte/elements";

  type Testimonial10Props = {
    quote?: string;
    author?: {
      name: string;
      role: string;
      avatar: {
        src: string;
        alt: string;
      };
    };
  };
</script>

<script lang="ts">
  let {
    quote = "Lorem ipsum dolor sit amet consectetur adipisicing elit. Elig doloremque mollitia fugiat omnis! Porro facilis quo animi consequatur. Explicabo.",
    author = {
      name: "Customer Name",
      role: "Role",
      avatar: {
        src: "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/avatar-1.webp",
        alt: "Customer Name",
      },
    },
    class: className,
    ...restProps
  }: Testimonial10Props & HTMLAttributes<HTMLElement> = $props();
</script>

<section class={cn("py-32", className)} {...restProps}>
  <div class="container">
    <div class="flex flex-col items-center text-center">
      <p class="mb-16 max-w-4xl px-8 font-medium lg:text-3xl">
        &ldquo;{quote}&rdquo;
      </p>
      <div class="flex items-center gap-2 md:gap-4">
        <Avatar.Root class="size-12 md:size-16">
          <Avatar.Image src={author.avatar.src} alt={author.avatar.alt} />
          <Avatar.Fallback>{author.name}</Avatar.Fallback>
        </Avatar.Root>
        <div class="text-left">
          <p class="text-sm font-medium md:text-base">{author.name}</p>
          <p class="text-sm text-muted-foreground md:text-base">
            {author.role}
          </p>
        </div>
      </div>
    </div>
  </div>
</section>
