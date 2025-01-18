<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';
	import samples from '$lib/img/docs/quick/samples.png';
	import window from '$lib/img/docs/quick/window.png';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Quick Start</Heading>
<div class="p-4">
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>1 - Import Game Library</Heading
	>
	<P class="mb-2">
		Start by importing <strong class="font-extrabold text-rose-400">Library</strong>.
	</P>
	<P class="mb-2">
		The library sample includes dependencies required by other samples. Without it, the samples will not function.
	</P>
	<img alt="samples" src={samples} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>2 - Import Game Sample</Heading
	>
	<P class="mb-2">
		Import one the game samples. <strong class="font-extrabold text-rose-400">Game</strong> or if
		you prefer addressables version,
		<strong class="font-extrabold text-rose-400">Game Addressables</strong>.
	</P>
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>3 - Setup Game Sample</Heading
	>
	<P class="mb-0"
		>Luna UI Panel should open. If it didn't, open it via <strong
			class="font-extrabold text-rose-400">Tools > Cupkek Games > Luna UI Panel</strong
		></P
	>
	<P class="mb-0">Complete setup by clicking buttons.</P>
	<P class="mb-0"
		><strong class="font-extrabold">Game</strong> adds demo scenes to Build Settings.</P
	>
	<P class="mb-2"
		><strong class="font-extrabold">Game Addressables</strong> makes demo scenes addressable.</P
	>
	<img alt="window" src={window} class="mb-6 max-w-xs rounded-xl border-4" />
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>4 - Ready!</Heading
	>
	<P class="mb-0"
		>Go to <strong class="font-extrabold text-rose-400">Assets/Samples/LunaUI/</strong> to find demo
		folder.</P
	>
	<P class="mb-0">You can open and start the initialization scene.</P>
</div>
