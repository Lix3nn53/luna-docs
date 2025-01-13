<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';
	import reimport from '$lib/img/docs/troubleshoot/reimport.jpg';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Troubleshoot</Heading
>
<div class="p-4">
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Styles Failing to Load Properly</Heading
	>
	<P class="mb-2">
		Sometimes, USS files fail to import correctly, requiring manual re-importing. Go to <strong
			class="font-extrabold text-rose-400">Packages > Luna UI > Runtime > USS</strong
		>.
	</P>
	<P class="mb-2">
		We have to do this for all folders in here. Make sure to go into each folder and perform this
		action on the files inside, not on the folder itself. Here's what to do: Select all fies by ctrl
		+ a > right click > Reimport.
	</P>
	<P class="mb-2">
		Do <strong class="font-extrabold text-rose-400">NOT</strong> click "Reimport All", make sure you
		click <strong class="font-extrabold text-lime-400">"Reimport"</strong>.
	</P>
	<img alt="samples" src={reimport} class="mb-6 max-w-lg rounded-xl border-4" />
	<P class="mb-2">
		Styles should work properly now. If they don't, try reimporting the: Packages > Luna UI >
		Runtime > Setup > CupkekGamesMainTheme.
	</P>
</div>
