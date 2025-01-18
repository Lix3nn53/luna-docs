<script lang="ts">
	import { page } from '$app/stores';
	import { onDestroy } from 'svelte';
	import { Button } from 'flowbite-svelte';

	import { A } from 'flowbite-svelte';
	import logo from '$lib/img/logo128.png';

	let path: string = $page.url.pathname;

	let routes: { name: string; path: string; target: '_blank' | '_self' }[] = [];
	$: routes = [
		{ name: 'Hero Manager', path: '/', target: '_self' },
		{ name: 'Presskit', path: '/presskit', target: '_self' },
		{ name: 'GameDev Tools', path: 'https://docs.cupkek.games/', target: '_blank' }
	];

	let navigation: HTMLDivElement;
	function toggle() {
		navigation.classList.toggle('hidden');
	}
</script>

<nav class="px-2 sm:px-4 py-2.5 bg-stone-800">
	<div class="md:container flex flex-col gap-2 md:flex-row justify-between items-center">
		<div class="flex flex-row w-full md:w-auto">
			<button
				data-collapse-toggle="mobile-menu-4"
				type="button"
				class="inline-flex items-center rounded-lg px-4 md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 hover:bg-gray-700 focus:ring-gray-600"
				aria-controls="mobile-menu-4"
				aria-expanded="false"
				on:click={() => toggle()}
			>
				<span class="sr-only">Open main menu</span>
				<svg
					class="w-6 h-6"
					fill="currentColor"
					viewBox="0 0 20 20"
					xmlns="http://www.w3.org/2000/svg"
					><path
						fill-rule="evenodd"
						d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z"
						clip-rule="evenodd"
					/></svg
				>
				<svg
					class="hidden w-6 h-6"
					fill="currentColor"
					viewBox="0 0 20 20"
					xmlns="http://www.w3.org/2000/svg"
					><path
						fill-rule="evenodd"
						d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
						clip-rule="evenodd"
					/></svg
				>
			</button>
			<A href="/" style="ghost">
				<div class="h-14 flex flex-row justify-center items-center gap-1">
					<img src={logo} class="h-14" alt="Logo" />
					<span>Cupkek Games</span>
				</div>
			</A>
		</div>
		<div class="md:order-2 flex justify-around gap-2 min-h-12 flex-1 sm:flex-none">
			<Button
				href="https://discord.com/invite/k3yj8Az2VC"
				target="_blank"
				><i class="fa-brands fa-discord fa-xl"></i><span class="hidden md:flex ml-2">Discord</span
				></Button
			>
			<Button
				href="https://store.steampowered.com/app/2671700/Hero_Manager"
				target="_blank"
				><i class="fa-brands fa-steam fa-xl"></i><span class="hidden md:flex ml-2"
					>Wishlist Now!</span
				></Button
			>
		</div>
		<div
			class="hidden justify-around items-center flex-1 md:flex md:w-auto md:order-1"
			id="mobile-menu-4"
			bind:this={navigation}
		>
			<ul class="flex flex-col mt-4 md:flex-row md:space-x-8 md:mt-0 md:font-medium">
				{#each routes as route, i}
					{#if path === route.path}
						<li class="py-4 md:py-0">
							<Button href={`${route.path}`} target={`${route.target}`} style="ghost"
								>{route.name}</Button
							>
						</li>
					{:else}
						<li class="py-4 md:py-0">
							<Button href={`${route.path}`} target={`${route.target}`} style="ghost"
								>{route.name}</Button
							>
						</li>
					{/if}
				{/each}
			</ul>
		</div>
	</div>
</nav>
