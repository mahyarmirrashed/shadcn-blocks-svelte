<script lang="ts" module>
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
  <div class="flex flex-col gap-1 pt-1 sm:pl-3">
    <h2 class="font-medium capitalize opacity-80">{name}</h2>
    <h2 class="w-lg text-sm text-muted-foreground">
      {@render description()}
    </h2>
  </div>
  <div class="relative flex items-center justify-center p-4">
    {@render children?.()}
  </div>
</div>
