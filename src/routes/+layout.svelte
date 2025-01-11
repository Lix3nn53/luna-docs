<script context="module" lang="ts">
	import '../app.css';
	import Footer from '$lib/components/Footer.svelte';
	import Sidebar from '$lib/components/Sidebar.svelte';
	import Background from '$lib/components/Background.svelte';
	import BackgroundColor from '$lib/components/BackgroundColor.svelte';
	import { Alert } from 'flowbite-svelte';
</script>

<main class="flex-1 flex bg-stone-700 text-stone-50">
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
