<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';
	import reimport from '$lib/img/docs/troubleshoot/reimport.jpg';
	import uibuildertheme from '$lib/img/docs/troubleshoot/uibuildertheme.jpg';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Troubleshoot</Heading
>
<div class="p-4">
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Styles failing to load properly</Heading
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
	<img alt="samples" src={reimport} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<P class="mb-2">
		Styles should work properly now. If they don't, try reimporting the: Packages > Luna UI >
		Runtime > Setup > CupkekGamesMainTheme.
	</P>
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Styles not working in UI Builder</Heading
	>
	<P class="mb-2">Make sure you select the correct Theme.</P>
	<img alt="uibuildertheme" src={uibuildertheme} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
</div>
