<script lang="ts">
	import { page } from '$app/stores';
	import { onMount } from 'svelte';

	let status = 404;
	let message = 'Page not found';

	onMount(() => {
		// Get the error details from the page store
		status = $page.status || 404;
		message = $page.error?.message || getErrorMessage(status);
	});

	function getErrorMessage(status: number): string {
		switch (status) {
			case 404:
				return 'Page not found';
			case 500:
				return 'Internal server error';
			case 403:
				return 'Access forbidden';
			default:
				return 'Something went wrong';
		}
	}
</script>

<svelte:head>
	<title>{status} - {message}</title>
</svelte:head>

<div class="min-h-screen bg-stone-700 text-stone-50 flex items-center justify-center">
	<div class="text-center px-4">
		<h1 class="text-9xl font-bold text-violet-400 mb-4">{status}</h1>
		<h2 class="text-2xl font-semibold mb-6 text-stone-100">{message}</h2>
		<p class="text-stone-300 mb-8 max-w-md mx-auto">
			{#if status === 404}
				The page you're looking for doesn't exist or has been moved.
			{:else}
				Something went wrong. Please try again later.
			{/if}
		</p>
		<div class="space-x-4">
			<a href="/" class="inline-flex items-center px-6 py-3 bg-violet-500 hover:bg-violet-600 text-white font-medium rounded-lg transition-colors">
				<i class="fa-solid fa-home mr-2"></i>
				Go Home
			</a>
		</div>
	</div>
</div>