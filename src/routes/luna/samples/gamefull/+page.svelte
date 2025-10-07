<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Alert } from 'flowbite-svelte';
	import samples from '$lib/img/docs/quick/samples.png';
	import window from '$lib/img/docs/quick/window.png';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Sample/ Game Full</Heading
>
<div class="p-4">
	<P class="mb-2">
		A complete game demo featuring settings, save/load functionality, and a showcase of Luna UI's
		capabilities.
	</P>
	<P class="mb-2">Uses standart single scene workflow.</P>
	<P class="mb-2">
		Refer to <A color="text-sky-400 font-extrabold" href="/luna/quickstart">quickstart</A> to get started.
	</P>
	
	<Alert border class="my-4">
		<div class="flex flex-row">
			<i class="fa-solid fa-lightbulb fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-2">
					<b>Difference with Game Standard sample:</b> This sample combines Game Standard with Localization and Newtonsoft samples. Adding localization and working save load system. Requires Newtonsoft and Unity's Localization packages.
				</P>
			</div>
		</div>
	</Alert>
</div>
