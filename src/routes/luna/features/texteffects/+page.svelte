<script lang="ts">
  import { Heading } from 'flowbite-svelte';
  import { onMount } from 'svelte';
  import { marked } from 'marked';
  import texteffects from '$lib/docs/texteffects.txt?raw';
  import textEffectsGif from '$lib/img/docs/features/TextEffects.gif';

  let parsedContent: string = '';

  onMount(async () => {
    parsedContent = await marked.parse(texteffects);
  });
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Features/ Text Effects</Heading>

<div class="p-2 lg:p-4 xl:p-8 h-full space-y-8">
  <img alt="Text Effects" src={textEffectsGif} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
  {#if parsedContent}
    <div class="prose prose-invert max-w-none">
      {@html parsedContent}
    </div>
  {:else}
    <div class="flex justify-center items-center h-32">
      <div class="text-stone-400">Loading text effects guide...</div>
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
    margin-bottom: 1rem;
  }
  :global(.prose h2) {
    color: #60a5fa;
    font-size: 1.25rem;
    font-weight: bold;
    margin-top: 1.5rem;
    margin-bottom: 0.75rem;
  }
  :global(.prose h3) {
    color: #93c5fd;
    font-size: 1.1rem;
    font-weight: bold;
    margin-top: 1.25rem;
    margin-bottom: 0.5rem;
  }
  :global(.prose h4) {
    color: #93c5fd;
    font-size: 1rem;
    font-weight: bold;
    margin-top: 1rem;
    margin-bottom: 0.5rem;
  }
  :global(.prose p) {
    margin: 0.75rem 0;
    color: #e5e7eb;
    line-height: 1.6;
  }
  :global(.prose ul) {
    list-style-type: disc;
    padding-left: 1.5rem;
    margin: 0.75rem 0;
  }
  :global(.prose ol) {
    list-style-type: decimal;
    padding-left: 1.5rem;
    margin: 0.75rem 0;
  }
  :global(.prose li) {
    margin: 0.5rem 0;
    color: #e5e7eb;
  }
  :global(.prose li::marker) {
    color: #e5e7eb;
  }
  :global(.prose code) {
    background-color: #374151;
    color: #fbbf24;
    padding: 0.125rem 0.375rem;
    border-radius: 0.25rem;
    font-size: 0.875em;
  }
  :global(.prose pre) {
    background-color: #1f2937;
    padding: 1rem;
    border-radius: 0.5rem;
    overflow-x: auto;
    margin: 1rem 0;
  }
  :global(.prose pre code) {
    background-color: transparent;
    color: #e5e7eb;
    padding: 0;
  }
  :global(.prose strong) {
    color: #fbbf24;
    font-weight: bold;
  }
  :global(.prose a) {
    color: #60a5fa;
    text-decoration: underline;
  }
  :global(.prose a:hover) {
    color: #93c5fd;
  }
  :global(.prose hr) {
    border-color: #4b5563;
    margin: 2rem 0;
  }
  :global(.prose blockquote) {
    border-left: 4px solid #4b5563;
    padding-left: 1rem;
    margin: 1rem 0;
    color: #9ca3af;
  }
  :global(.prose table) {
    width: 100%;
    border-collapse: collapse;
    margin: 1rem 0;
  }
  :global(.prose th) {
    background-color: #374151;
    color: #e5e7eb;
    padding: 0.5rem;
    text-align: left;
    border: 1px solid #4b5563;
  }
  :global(.prose td) {
    padding: 0.5rem;
    border: 1px solid #4b5563;
    color: #e5e7eb;
  }
</style>

