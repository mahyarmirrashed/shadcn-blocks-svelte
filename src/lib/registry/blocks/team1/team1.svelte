<script lang="ts" module>
  import * as Avatar from "$lib/registry/ui/avatar/index.js";
  import { cn } from "$lib/utils.js";
  import type { HTMLAttributes } from "svelte/elements";

  type TeamMember = {
    id: string;
    name: string;
    role: string;
    avatar: string;
  };

  export type Team1Props = {
    heading?: string;
    subheading?: string;
    description?: string;
    members?: TeamMember[];
  };
</script>

<script lang="ts">
  let {
    heading = "Team",
    description = "Our diverse team of experts brings together decades of experience in design, engineering, and product development.",
    members = [
      {
        id: "member-1",
        name: "Sarah Chen",
        role: "CEO & Founder",
        avatar:
          "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/avatar-1.webp",
      },
      {
        id: "member-2",
        name: "Marcus Rodriguez",
        role: "CTO",
        avatar:
          "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/avatar-2.webp",
      },
      {
        id: "member-3",
        name: "Emily Watson",
        role: "Head of Design",
        avatar:
          "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/avatar-3.webp",
      },
      {
        id: "member-4",
        name: "David Kim",
        role: "Lead Engineer",
        avatar:
          "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/avatar-4.webp",
      },
      {
        id: "member-5",
        name: "Lisa Thompson",
        role: "Product Manager",
        avatar:
          "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/avatar-5.webp",
      },
      {
        id: "member-6",
        name: "Alex Johnson",
        role: "UX Designer",
        avatar:
          "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/avatar-6.webp",
      },
    ],
    class: className,
    ...restProps
  }: Team1Props & HTMLAttributes<HTMLElement> = $props();
</script>

<section class={cn("py-32", className)} {...restProps}>
  <div class="container flex flex-col items-center text-center">
    <h2 class="my-6 text-2xl font-bold text-pretty lg:text-4xl">
      {heading}
    </h2>
    <p class="mb-8 max-w-3xl text-muted-foreground lg:text-xl">
      {description}
    </p>
  </div>
  <div
    class="container mt-16 grid gap-x-8 gap-y-16 md:grid-cols-2 lg:grid-cols-3"
  >
    {#each members as member (member.id)}
      <div class="flex flex-col items-center">
        <Avatar.Root class="mb-4 size-20 border md:mb-5 lg:size-24">
          <Avatar.Image src={member.avatar} />
          <Avatar.Fallback>{member.name}</Avatar.Fallback>
        </Avatar.Root>
        <p class="text-center font-medium">{member.name}</p>
        <p class="text-center text-muted-foreground">{member.role}</p>
      </div>
    {/each}
  </div>
</section>
