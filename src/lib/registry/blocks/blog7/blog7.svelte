<script lang="ts" module>
  import { Badge } from "$lib/registry/ui/badge/index.js";
  import { Button } from "$lib/registry/ui/button/index.js";
  import * as Card from "$lib/registry/ui/card/index.js";
  import { cn } from "$lib/utils.js";
  import Icon from "@iconify/svelte";
  import type { HTMLAttributes } from "svelte/elements";

  type Post = {
    title: string;
    summary: string;
    author: string;
    publishDate: string;
    url: string;
    image: { src: string; alt: string };
  };

  export type Blog7Props = {
    tagline?: string;
    heading?: string;
    description?: string;
    button?: {
      text: string;
      url: string;
    };
    posts?: Post[];
  };
</script>

<script lang="ts">
  let {
    tagline = "Latest Updates",
    heading = "Blog Posts",
    description = "Discover the latest trends, tips, and best practices in modern web development. From UI components to design systems, stay updated with our expert insights.",
    button = {
      text: "View all articles",
      url: "https://shadcnblocks.com",
    },
    posts = [
      {
        title: "Getting Started with shadcn/ui Components",
        summary:
          "Learn how to quickly integrate and customize shadcn/ui components in your Next.js projects. We'll cover installation, theming, and best practices for building modern interfaces.",
        author: "Sarah Chen",
        publishDate: "1 Jan 2024",
        url: "https://shadcnblocks.com",
        image: {
          src: "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/placeholder-dark-1.svg",
          alt: "Generic alternate text",
        },
      },
      {
        title: "Building Accessible Web Applications",
        summary:
          "Explore how to create inclusive web experiences using shadcn/ui's accessible components. Discover practical tips for implementing ARIA labels, keyboard navigation, and semantic HTML.",
        author: "Marcus Rodriguez",
        publishDate: "1 Jan 2024",
        url: "https://shadcnblocks.com",
        image: {
          src: "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/placeholder-dark-1.svg",
          alt: "Generic alternate text",
        },
      },
      {
        title: "Modern Design Systems with Tailwind CSS",
        summary:
          "Dive into creating scalable design systems using Tailwind CSS and shadcn/ui. Learn how to maintain consistency while building flexible and maintainable component libraries.",
        author: "Emma Thompson",
        publishDate: "1 Jan 2024",
        url: "https://shadcnblocks.com",
        image: {
          src: "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/placeholder-dark-1.svg",
          alt: "Generic alternate text",
        },
      },
    ],
    class: className,
    ...restProps
  }: Blog7Props & HTMLAttributes<HTMLElement> = $props();
</script>

<section class={cn("py-32", className)} {...restProps}>
  <div class="container mx-auto flex flex-col items-center gap-16 lg:px-16">
    <div class="text-center">
      <Badge variant="secondary" class="mb-6">
        {tagline}
      </Badge>
      <h2
        class="mb-3 text-3xl font-semibold text-pretty md:mb-4 md:text-4xl lg:mb-6 lg:max-w-3xl lg:text-5xl"
      >
        {heading}
      </h2>
      <p
        class="mb-8 text-muted-foreground md:text-base lg:max-w-2xl lg:text-lg"
      >
        {description}
      </p>
      <Button
        variant="link"
        href={button.url}
        target="_blank"
        class="w-full sm:w-auto"
      >
        {button.text}
        <Icon icon="lucide:arrow-right" class="ml-2 size-4" />
      </Button>
    </div>
    <div class="grid gap-6 md:grid-cols-2 lg:grid-cols-3 lg:gap-8">
      {#each posts as post}
        <Card.Root class="grid grid-rows-[auto_auto_1fr_auto] pt-0">
          <div class="aspect-16/9 w-full">
            <a
              href={post.url}
              target="_blank"
              class="transition-opacity duration-200 fade-in hover:opacity-70"
            >
              <img
                src={post.image.src}
                alt={post.image.alt}
                class="h-full w-full object-cover object-center"
              />
            </a>
          </div>
          <Card.Header>
            <h3 class="text-lg font-semibold hover:underline md:text-xl">
              <a href={post.url} target="_blank">
                {post.title}
              </a>
            </h3>
          </Card.Header>
          <Card.Content>
            <p class="text-muted-foreground">{post.summary}</p>
          </Card.Content>
          <Card.Footer>
            <a
              href={post.url}
              target="_blank"
              class="flex items-center text-foreground hover:underline"
            >
              Read more
              <Icon icon="lucide:arrow-right" class="ml-2 size-4" />
            </a>
          </Card.Footer>
        </Card.Root>
      {/each}
    </div>
  </div>
</section>
