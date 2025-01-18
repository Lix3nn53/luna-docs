<script lang="ts">
	import '../app.css';
	import { page } from '$app/state';
	import { sineIn } from 'svelte/easing';
	import { fly, fade } from 'svelte/transition'

	import Footer from '$lib/components/Footer.svelte';
	import Sidebar from '$lib/components/Sidebar.svelte';
	import BackgroundColor from '$lib/components/BackgroundColor.svelte';
  import Toc from 'svelte-toc';
	import logo from '$lib/img/logo128.png';

	import {
		Navbar,
		NavHamburger,
		NavUl,
		NavLi,
		CloseButton,
		DarkMode,
		NavBrand
	} from 'flowbite-svelte';

	import { onMount } from 'svelte';

	onMount(() => {
		mounted = true;
	});
	

	let breakPoint: number = 1024;
	let breakPointCurrent: boolean = true; // true = hight
	let mounted: boolean = false;
	let width: number;
	let sidebarHidden: boolean = false;
	let sidebarContainer: HTMLDivElement;
	let sidebarButton: HTMLButtonElement;
	let navbarHidden: boolean = true;
	let navbarButton: HTMLButtonElement;

	$: if (width >= breakPoint) {
			navbarButton.classList.remove('rotate-180');
			
			if (sidebarContainer != null) {
				sidebarContainer.classList.remove('absolute');
			}

			if (mounted && !breakPointCurrent ) {
				navbarHidden = true;
				sidebarHidden = false;
				breakPointCurrent = true;
			}
	} else {
		if (sidebarContainer != null) {
			sidebarContainer.classList.add('absolute');
		}

		if (mounted && breakPointCurrent) {
			sidebarHidden = true;
			breakPointCurrent = false;
		}
	}

	const toggleSide = () => {
		sidebarHidden = !sidebarHidden;

		if (width < breakPoint) {
			sidebarButton.classList.toggle('rotate-90');
			sidebarButton.classList.toggle('-rotate-90');
		}
	};

	const toggleNavbar = () => {
		navbarHidden = !navbarHidden;
		navbarButton.classList.toggle('rotate-180');
	};
</script>

<svelte:window bind:innerWidth={width} />

<BackgroundColor />
<header class="flex-none w-full bg-white">
	<Navbar class="flex flex-wrap justify-between items-center dark:bg-yellow-300 p-0">
		<div class="flex flex-row items-center min-h-12 lg:min-h-none dark:text-black">
			<button aria-label="expand-navbar" on:click={toggleSide} class="flex md:flex lg:hidden transition-transform dark:hover:bg-yellow-100 p-3 rounded-lg rotate-90" bind:this={sidebarButton}>
				<i class="fa-solid fa-angles-down"></i>
			</button>
			<NavBrand href="/">
				<img src={logo} alt="logo" class="max-w-8">
				<span class="whitespace-nowrap text-xl font-semibold pl-4 ml-0">
					CupkekGames Tools
				</span>
			</NavBrand>
		</div>
		<NavUl
			hidden={navbarHidden}
			divClass="w-full lg:block lg:w-auto order-1 lg:order-none"
			ulClass="flex flex-col lg:flex-row text-md font-bold gap-4 p-4 lg:p-0 my-4 lg:my-0 dark:bg-yellow-300 border-0"
			slideParams={{delay: 100, duration: 200, easing: sineIn }}
			activeUrl={page.url.pathname}
			nonActiveClass="text-black"
			activeClass="text-black"
		>
		<NavLi class="flex flex-row justify-end" href="https://discord.com/invite/k3yj8Az2VC" target="_blank"
			>Discord<i class="fa-solid fa-up-right-from-square ml-1 flex items-center"></i></NavLi
		>
		<NavLi class="flex flex-row justify-end"
			>Buy on the Asset Store<i class="fa-solid fa-up-right-from-square ml-1 flex items-center"></i></NavLi
		>
		</NavUl>
		<div class="flex flex-row items-center dark:text-black flex md:flex lg:hidden">
				<button aria-label="expand-navbar" on:click={toggleNavbar} class="flex md:flex lg:hidden transition-transform dark:hover:bg-yellow-100 p-3 rounded-lg" bind:this={navbarButton}>
					<i class="fa-solid fa-angles-down"></i>
				</button>
		</div>
	</Navbar>
</header>

<!-- relative makes sidebar absolute full height -->
<main class="flex-1 flex text-stone-50 container bg-stone-700 mx-auto min-h-full relative">
	<div class="flex-1 flex flex-col min-h-full">
		<div class="flex-1 flex flex-row min-h-full">
			{#if !sidebarHidden}
			<div
			class="w-64 inset-y-0 left-0 min-h-full z-50"
			id="sidebar"
			bind:this={sidebarContainer}
			transition:fly={{ x: -200 }}
			>
				<div class="flex justify-end bg-stone-800">
					<CloseButton on:click={toggleSide} class="m-4 dark:text-white lg:hidden" />
				</div>
				<Sidebar />
			</div>
			{/if}
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
