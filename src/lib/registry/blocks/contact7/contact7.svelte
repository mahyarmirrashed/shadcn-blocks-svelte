<script lang="ts" module>
  import { cn } from "$lib/utils.js";
  import Icon from "@iconify/svelte";
  import type { HTMLAttributes } from "svelte/elements";

  export type Contact7Props = {
    title?: string;
    description?: string;
    emailLabel?: string;
    emailDescription?: string;
    email?: string;
    officeLabel?: string;
    officeDescription?: string;
    officeAddress?: string;
    phoneLabel?: string;
    phoneDescription?: string;
    phone?: string;
    chatLabel?: string;
    chatDescription?: string;
    chatLink?: string;
  };
</script>

<script lang="ts">
  let {
    title = "Contact Us",
    description = "Contact the support team at Shadcnblocks.",
    emailLabel = "Email",
    emailDescription = "We respond to all emails within 24 hours.",
    email = "example@shadcnblocks.com",
    officeLabel = "Office",
    officeDescription = "Drop by our office for a chat.",
    officeAddress = "1 Eagle St, Brisbane, QLD, 4000",
    phoneLabel = "Phone",
    phoneDescription = "We're available Mon-Fri, 9am-5pm.",
    phone = "+123 456 7890",
    chatLabel = "Live Chat",
    chatDescription = "Get instant help from our support team.",
    chatLink = "Start Chat",
    class: className,
    ...restProps
  }: Contact7Props & HTMLAttributes<HTMLElement> = $props();
</script>

<section class={cn("py-32", className)} {...restProps}>
  <div class="container">
    <div class="mb-14">
      <h1 class="mt-2 mb-3 text-3xl font-semibold text-balance md:text-4xl">
        {title}
      </h1>
      <p class="max-w-xl text-lg text-muted-foreground">
        {description}
      </p>
    </div>
    <div class="grid gap-6 md:grid-cols-2">
      <div class="rounded-lg bg-muted p-6">
        <span
          class="mb-3 flex size-12 flex-col items-center justify-center rounded-full bg-accent"
        >
          <Icon icon="lucide:mail" class="h-6 w-auto" />
        </span>
        <p class="mb-2 text-lg font-semibold">{emailLabel}</p>
        <p class="mb-3 text-muted-foreground">{emailDescription}</p>
        <a href={`mailto:${email}`} class="font-semibold hover:underline">
          {email}
        </a>
      </div>
      <div class="rounded-lg bg-muted p-6">
        <span
          class="mb-3 flex size-12 flex-col items-center justify-center rounded-full bg-accent"
        >
          <Icon icon="lucide:map-pin" class="h-6 w-auto" />
        </span>
        <p class="mb-2 text-lg font-semibold">{officeLabel}</p>
        <p class="mb-3 text-muted-foreground">{officeDescription}</p>
        <a href="/" class="font-semibold hover:underline">
          {officeAddress}
        </a>
      </div>
      <div class="rounded-lg bg-muted p-6">
        <span
          class="mb-3 flex size-12 flex-col items-center justify-center rounded-full bg-accent"
        >
          <Icon icon="lucide:phone" class="h-6 w-auto" />
        </span>
        <p class="mb-2 text-lg font-semibold">{phoneLabel}</p>
        <p class="mb-3 text-muted-foreground">{phoneDescription}</p>
        <a href={`tel:${phone}`} class="font-semibold hover:underline">
          {phone}
        </a>
      </div>
      <div class="rounded-lg bg-muted p-6">
        <span
          class="mb-3 flex size-12 flex-col items-center justify-center rounded-full bg-accent"
        >
          <Icon icon="lucide:message-circle" class="h-6 w-auto" />
        </span>
        <p class="mb-2 text-lg font-semibold">{chatLabel}</p>
        <p class="mb-3 text-muted-foreground">{chatDescription}</p>
        <a href="/" class="font-semibold hover:underline">
          {chatLink}
        </a>
      </div>
    </div>
  </div>
</section>
