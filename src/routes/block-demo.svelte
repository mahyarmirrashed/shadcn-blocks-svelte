<script lang="ts" module>
  import Button from "$lib/components/ui/button/button.svelte";
  import Icon from "@iconify/svelte";
  import type { WithChildren } from "bits-ui";
  import type { Snippet } from "svelte";

  type Props = {
    name: string;
    description: Snippet;
  };
</script>

<script lang="ts">
  let { name, description, children }: WithChildren<Props> = $props();
</script>

<div class="relative flex flex-col gap-4 rounded-lg border p-4">
  <div class="flex justify-between">
    <div class="flex flex-col gap-1 pt-1 sm:pl-3">
      <h2 class="font-medium capitalize opacity-80">{name}</h2>
      <h2 class="w-lg text-sm text-muted-foreground">
        {@render description()}
      </h2>
    </div>
    <Button
      href={`https://www.shadcnblocks.com/block/${name}`}
      target="_blank"
      variant="outline"
      class="cursor-pointer"
      >View Original <Icon icon="lucide:external-link" /></Button
    >
  </div>
  <div class="relative flex items-center justify-center p-4">
    {@render children?.()}
  </div>
</div>
