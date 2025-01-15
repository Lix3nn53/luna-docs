<script context="module" lang="ts">
	import '../app.css';
	import Footer from '$lib/components/Footer.svelte';
	import Sidebar from '$lib/components/Sidebar.svelte';
	import BackgroundColor from '$lib/components/BackgroundColor.svelte';
  import Toc from 'svelte-toc';
	
</script>

<BackgroundColor />

<main class="flex-1 flex bg-stone-700 text-stone-50 container mx-auto">
	<Sidebar />
	<div class="flex-1 flex flex-col">
		<div class="flex-1 flex flex-col">
			<div class="p-4 flex flex-row justify-between">
				<div class="max-w-5xl">
					<slot />
				</div>
				<div class="toc-container border-l border-stone-500">
					<Toc />
				</div>
			</div>
		</div>
		<Footer />
	</div>
</main>

<style lang="css">
	:root {
    --toc-min-width: 256px; /* Default value for larger screens */
		--toc-width: 256px;
		--toc-active-bg: #8b5cf6;
		--toc-li-hover-color: #e879f9;
  }

	.toc-container {
		min-width: var(--toc-min-width);
		width: var(--toc-width);
	}

  @media (max-width: 1024) {
    :root {
      --toc-min-width: 128px; /* Smaller value for medium screens */
			--toc-width: 128px;
    }
  }

  @media (max-width: 768px) {
    :root {
      --toc-min-width: 0; /* Disappear for small screens */
			--toc-width: 0;
    }

    .toc-container {
      display: none;
    }
  }
</style>
