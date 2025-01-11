<script context="module" lang="ts">
	import '../app.css';
	import Footer from '$lib/components/Footer.svelte';
	import Sidebar from '$lib/components/Sidebar.svelte';
	import BackgroundColor from '$lib/components/BackgroundColor.svelte';
	
</script>

<BackgroundColor />

<main class="flex-1 flex bg-stone-700 text-stone-50 container mx-auto">
	<Sidebar />
	<div class="flex-1 flex flex-col">
		<div class="flex-1 flex flex-col">
			<slot />
		</div>
		<Footer />
	</div>
</main>


<style>
</style>
