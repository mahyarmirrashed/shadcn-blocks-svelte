<script lang="ts" module>
  import * as Accordion from "$lib/registry/ui/accordion/index.js";
  import { cn } from "$lib/utils.js";
  import type { HTMLAttributes } from "svelte/elements";

  type FaqItem = {
    question: string;
    answer: string;
  };

  type Faq1Props = {
    heading?: string;
    items?: FaqItem[];
  };
</script>

<script lang="ts">
  let {
    heading = "Frequently asked questions",
    items = [
      {
        question: "What is a FAQ?",
        answer:
          "A FAQ is a list of frequently asked questions and answers on a particular topic.",
      },
      {
        question: "What is the purpose of a FAQ?",
        answer:
          "The purpose of a FAQ is to provide answers to common questions and help users find the information they need quickly and easily.",
      },
      {
        question: "How do I create a FAQ?",
        answer:
          "To create a FAQ, you need to compile a list of common questions and answers on a particular topic and organize them in a clear and easy-to-navigate format.",
      },
      {
        question: "What are the benefits of a FAQ?",
        answer:
          "The benefits of a FAQ include providing quick and easy access to information, reducing the number of support requests, and improving the overall user experience.",
      },
      {
        question: "How should I organize my FAQ?",
        answer:
          "You should organize your FAQ in a logical manner, grouping related questions together and ordering them from most basic to more advanced topics.",
      },
      {
        question: "How long should FAQ answers be?",
        answer:
          "FAQ answers should be concise and to the point, typically a few sentences or a short paragraph is sufficient for most questions.",
      },
      {
        question: "Should I include links in my FAQ?",
        answer:
          "Yes, including links to more detailed information or related resources can be very helpful for users who want to learn more about a particular topic.",
      },
    ],
    class: className,
    ...restProps
  }: Faq1Props & HTMLAttributes<HTMLElement> = $props();
</script>

<section class={cn("py-32", className)} {...restProps}>
  <div class="container mx-auto max-w-3xl">
    <h1 class="mb-4 text-3xl font-semibold md:mb-11 md:text-4xl">
      {heading}
    </h1>
    <Accordion.Root type="single">
      {#each items as item, idx}
        <Accordion.Item value={`item-${idx}`}>
          <Accordion.Trigger class="font-semibold hover:no-underline">
            {item.question}
          </Accordion.Trigger>
          <Accordion.Content class="text-muted-foreground">
            {item.answer}
          </Accordion.Content>
        </Accordion.Item>
      {/each}
    </Accordion.Root>
  </div>
</section>
