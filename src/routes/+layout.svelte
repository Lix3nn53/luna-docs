<script lang="ts">
	import '../app.css';
	import Footer from '$lib/components/Footer.svelte';
	import Sidebar from '$lib/components/Sidebar.svelte';
	import BackgroundColor from '$lib/components/BackgroundColor.svelte';
  import Toc from 'svelte-toc';

	import {
		Navbar,
		NavHamburger,
		CloseButton,
	} from 'flowbite-svelte';
	

	let breakPoint: number = 1024;
	let width: number;
	let sidebarContainer: HTMLDivElement;

	$: if (width >= breakPoint) {
		if (sidebarContainer != null) {
			sidebarContainer.classList.remove('hidden');
			sidebarContainer.classList.remove('absolute');
		}
	} else {
		if (sidebarContainer != null) {
			sidebarContainer.classList.add('hidden');
			sidebarContainer.classList.add('absolute');
		}
	}

	const toggleSide = () => {
		if (width < breakPoint) {
			if (sidebarContainer != null) {
				sidebarContainer.classList.toggle('hidden');
			}
		}
	};
</script>

<svelte:window bind:innerWidth={width} />

<BackgroundColor />
<header class="flex-none w-full bg-white dark:bg-stone-900 lg:pl-64 md:flex lg:hidden">
	<Navbar class="flex flex-wrap justify-between items-center dark:bg-stone-400">
		<div class="flex flex-row items-center">
		<NavHamburger
		onClick={toggleSide}
			class="justify-between text-stone-950 focus:outline-none whitespace-normal rounded-lg focus:ring-2 p-1.5 focus:ring-stone-400 hover:bg-stone-100 dark:hover:bg-stone-600 m-0 mr-3 flex md:flex lg:hidden"
		/>
		</div>
	</Navbar>
</header>

<main class="flex-1 flex text-stone-50 container bg-stone-700 mx-auto min-h-full">
	<div class="flex-1 flex flex-col min-h-full">
		<div class="flex-1 flex flex-row min-h-full">
			<div
			class="w-64 inset-y-0 left-0 min-h-full"
			id="sidebar"
			bind:this={sidebarContainer}
			>
				<div class="flex justify-end bg-stone-800">
					<CloseButton on:click={toggleSide} class="m-4 dark:text-white lg:hidden" />
				</div>
				<Sidebar />
			</div>
			<div class="p-4 flex-1 flex flex-row justify-between">
				<div class="flex-1">
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
    --toc-max-width: 256px; /* Default value for larger screens */
		--toc-width: 256px;
		--toc-active-bg: #8b5cf6;
		--toc-li-hover-color: #e879f9;
  }

	.toc-container {
		min-width: var(--toc-min-width);
		max-width: var(--toc-max-width);
		width: var(--toc-width);
	}

  @media (max-width: 1280px) {
    :root {
      --toc-min-width: 0; /* Disappear for small screens */
			--toc-width: 0;
    }

    .toc-container {
      display: none;
    }
  }
</style>
