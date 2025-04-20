<script lang="ts">
  import { Heading, P, A, Mark, Gallery, GradientButton, Hr } from 'flowbite-svelte';
  import { Carousel, Thumbnails, Button, Indicator } from 'flowbite-svelte';
  import { onMount } from 'svelte';
  import { marked } from 'marked';

  let releaseNotes = '';
  let parsedNotes: string = '';

  onMount(async () => {
    const response = await fetch('/src/lib/docs/releasenotes.txt');
    releaseNotes = await response.text();
    parsedNotes = await marked.parse(releaseNotes);
  });
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Luna/ Release Notes</Heading>

<div class="p-2 lg:p-4 xl:p-8 h-full space-y-8">
  {#if parsedNotes}
    <div class="prose prose-invert max-w-none">
      {@html parsedNotes}
    </div>
  {:else}
    <div class="flex justify-center items-center h-32">
      <div class="text-stone-400">Loading release notes...</div>
    </div>
  {/if}
</div>

<style>
  :global(.prose) {
    color: #e5e7eb;
  }
  :global(.prose h1) {
    color: #60a5fa;
    font-size: 1.5rem;
    font-weight: bold;
    margin-top: 1.5rem;
  }
  :global(.prose ul) {
    list-style-type: disc;
    padding-left: 1.5rem;
  }
  :global(.prose li) {
    margin: 0.5rem 0;
    color: #e5e7eb;
  }
  :global(.prose li::marker) {
    color: #e5e7eb;
  }
</style>