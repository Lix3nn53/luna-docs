<script>
	import { Heading, P, A, List, Li, GradientButton, Hr } from 'flowbite-svelte';

	import banner from '$lib/img/docs/gallery/banner_2.jpg';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Introduction</Heading
>
<div class="p-4">
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		><i class="fa-solid fa-moon mr-2"></i>Luna UI</Heading
	>
	<img alt="banner" src={banner} class="mb-4 xl:max-w-xl max-w-full rounded-xl border-4" />
	<P class="mb-4"
		>Luna UI is built on top of Unity's UI Toolkit, offering simple solutions for common UI
		challenges without imposing any limitations on the UI Toolkit.</P
	>
	<GradientButton color="redToYellow" href="/luna/gallery">
		Learn more
		<i class="fa-solid fa-right-long ms-2 flex items-center"></i>
	</GradientButton>
	<Heading tag="h2" class="mb-4 mt-8" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		><i class="fa-solid fa-gears fa-sm mr-2"></i>Core Library</Heading
	>
	<P class="mb-6"
		>The Core Library provides essential utilities, and base functionality for Luna UI and Systems Library.</P
	>
	<Heading tag="h2" class="mb-4 mt-8" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		><i class="fa-solid fa-wrench fa-sm mr-2"></i>Systems Library</Heading
	>
	<P class="mb-2">OPTIONAL</P>
	<P class="">The Systems Library is entirely optional and is not part of the codebase until you import the Library sample, which includes all necessary dependencies for other samples.</P>  
	<P class="mb-6">Thanks to the Systems Library, the game samples in Luna UI are fully functional, not just visual.</P>
	<P class="mb-6">The Systems Library provides a great head start by offering fully functional game samples. 
		However, if you prefer to use your own systems, you can easily explore how the samples work and integrate your custom systems with the UI.</P>
</div>
