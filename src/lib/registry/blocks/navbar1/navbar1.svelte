<script lang="ts" module>
  import * as Accordion from "$lib/registry/ui/accordion/index.js";
  import { Button } from "$lib/registry/ui/button/index.js";
  import * as NavigationMenu from "$lib/registry/ui/navigation-menu/index.js";
  import * as Sheet from "$lib/registry/ui/sheet/index.js";
  import { cn } from "$lib/utils.js";
  import Icon from "@iconify/svelte";
  import type { HTMLAttributes } from "svelte/elements";

  type MenuItem = {
    title: string;
    url: string;
    description?: string;
    icon?: string;
    items?: MenuItem[];
  };

  type Navbar1Props = {
    logo?: {
      url: string;
      src: string;
      alt: string;
      title: string;
    };
    menu?: MenuItem[];
    auth?: {
      login: {
        title: string;
        url: string;
      };
      signup: {
        title: string;
        url: string;
      };
    };
  };
</script>

<script lang="ts">
  let {
    logo = {
      url: "https://www.shadcnblocks.com",
      src: "https://deifkwefumgah.cloudfront.net/shadcnblocks/block/logos/shadcnblockscom-icon.svg",
      alt: "logo",
      title: "Shadcnblocks.com",
    },
    menu = [
      { title: "Home", url: "#" },
      {
        title: "Products",
        url: "#",
        items: [
          {
            title: "Blog",
            description: "The latest industry news, updates, and info",
            icon: "lucide:book",
            url: "#",
          },
          {
            title: "Company",
            description: "Our mission is to innovate and empower the world",
            icon: "lucide:trees",
            url: "#",
          },
          {
            title: "Careers",
            description: "Browse job listings and discover our workspace",
            icon: "lucide:sunset",
            url: "#",
          },
          {
            title: "Support",
            description:
              "Get in touch with our support team or visit our community forums",
            icon: "lucide:zap",
            url: "#",
          },
        ],
      },
      {
        title: "Resources",
        url: "#",
        items: [
          {
            title: "Help Center",
            description: "Get all the answers you need right here",
            icon: "lucide:zap",
            url: "#",
          },
          {
            title: "Contact Us",
            description: "We are here to help you with any questions you have",
            icon: "lucide:sunset",
            url: "#",
          },
          {
            title: "Status",
            description: "Check the current status of our services and APIs",
            icon: "lucide:trees",
            url: "#",
          },
          {
            title: "Terms of Service",
            description: "Our terms and conditions for using our services",
            icon: "lucide:book",
            url: "#",
          },
        ],
      },
      { title: "Pricing", url: "#" },
      { title: "Blog", url: "#" },
    ],
    auth = {
      login: { title: "Login", url: "#" },
      signup: { title: "Sign up", url: "#" },
    },
    class: className,
    ...restProps
  }: Navbar1Props & HTMLAttributes<HTMLElement> = $props();
</script>

{#snippet Navbar1SubMenuLink(item: MenuItem)}
  <a
    class="flex min-w-80 flex-row gap-4 rounded-md p-3 leading-none no-underline transition-colors outline-none select-none hover:bg-muted hover:text-accent-foreground"
    href={item.url}
  >
    <div class="text-foreground">
      <Icon icon={item.icon ?? ""} class="size-5 shrink-0" />
    </div>
    <div>
      <div class="text-sm font-semibold">{item.title}</div>
      {#if item.description}
        <p class="text-sm leading-snug text-muted-foreground">
          {item.description}
        </p>
      {/if}
    </div>
  </a>
{/snippet}

{#snippet Navbar1MenuItem(item: MenuItem)}
  {#if item.items}
    <NavigationMenu.Item>
      <NavigationMenu.Trigger>{item.title}</NavigationMenu.Trigger>
      <NavigationMenu.Content class="bg-popover text-popover-foreground">
        <div class="p-2">
          {#each item.items as subItem (subItem.title)}
            <NavigationMenu.Link class="w-80">
              {#snippet child()}
                {@render Navbar1SubMenuLink(subItem)}
              {/snippet}
            </NavigationMenu.Link>
          {/each}
        </div>
      </NavigationMenu.Content>
    </NavigationMenu.Item>
  {:else}
    <NavigationMenu.Item>
      <NavigationMenu.Link
        href={item.url}
        class="group inline-flex h-10 w-max items-center justify-center rounded-md bg-background px-4 py-2 text-sm font-medium transition-colors hover:bg-muted hover:text-accent-foreground"
      >
        {item.title}
      </NavigationMenu.Link>
    </NavigationMenu.Item>
  {/if}
{/snippet}

{#snippet Navbar1MobileMenuItem(item: MenuItem)}
  {#if item.items}
    <Accordion.Item value={item.title} class="border-b-0">
      <Accordion.Trigger class="text-md py-0 font-semibold hover:no-underline">
        {item.title}
      </Accordion.Trigger>
      <Accordion.Content class="mt-2">
        {#each item.items as subItem (subItem.title)}
          {@render Navbar1SubMenuLink(subItem)}
        {/each}
      </Accordion.Content>
    </Accordion.Item>
  {:else}
    <a href={item.url} class="text-md font-semibold">{item.title}</a>
  {/if}
{/snippet}

<section class={cn("py-4", className)} {...restProps}>
  <div class="container">
    <nav class="hidden items-center justify-between lg:flex">
      <div class="flex items-center gap-6">
        <a href={logo.url} class="flex items-center gap-2">
          <img src={logo.src} alt={logo.alt} class="max-h-8 dark:invert" />
          <span class="text-lg font-semibold tracking-tighter"
            >{logo.title}</span
          >
        </a>
        <div class="flex items-center">
          <NavigationMenu.Root>
            <NavigationMenu.List>
              {#each menu as item (item.title)}
                {@render Navbar1MenuItem(item)}
              {/each}
            </NavigationMenu.List>
          </NavigationMenu.Root>
        </div>
      </div>
      <div class="flex gap-2">
        <Button asChild variant="outline" size="sm">
          <a href={auth.login.url}>{auth.login.title}</a>
        </Button>
        <Button asChild size="sm">
          <a href={auth.signup.url}>{auth.signup.title}</a>
        </Button>
      </div>
    </nav>

    <div class="block lg:hidden">
      <div class="flex items-center justify-between">
        <a href={logo.url} class="flex items-center gap-2">
          <img src={logo.src} alt={logo.alt} class="max-h-8 dark:invert" />
        </a>
        <Sheet.Root>
          <Sheet.Trigger>
            {#snippet children()}
              <Button variant="outline" size="icon">
                <Icon icon="lucide:menu" class="size-4" />
              </Button>
            {/snippet}
          </Sheet.Trigger>
          <Sheet.Content class="overflow-y-auto">
            <Sheet.Header>
              <Sheet.Title>
                <a href={logo.url} class="flex items-center gap-2">
                  <img
                    src={logo.src}
                    alt={logo.alt}
                    class="max-h-8 dark:invert"
                  />
                </a>
              </Sheet.Title>
            </Sheet.Header>
            <div class="flex flex-col gap-6 p-4">
              <Accordion.Root type="single" class="flex w-full flex-col gap-4">
                {#each menu as item (item.title)}
                  {@render Navbar1MobileMenuItem(item)}
                {/each}
              </Accordion.Root>
              <div class="flex flex-col gap-3">
                <Button asChild variant="outline">
                  <a href={auth.login.url}>{auth.login.title}</a>
                </Button>
                <Button asChild>
                  <a href={auth.signup.url}>{auth.signup.title}</a>
                </Button>
              </div>
            </div>
          </Sheet.Content>
        </Sheet.Root>
      </div>
    </div>
  </div>
</section>
