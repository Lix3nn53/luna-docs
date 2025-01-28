<script>
	import { Heading, P, A, Accordion, AccordionItem, Hr } from 'flowbite-svelte';
	import reimport from '$lib/img/docs/troubleshoot/reimport.jpg';
	import uibuildertheme from '$lib/img/docs/troubleshoot/uibuildertheme.jpg';
	import InputSettingsNoProjectWideAsset from '$lib/img/docs/troubleshoot/InputSettingsNoProjectWideAsset.png';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Troubleshoot</Heading
>
<div class="p-4">
	
	<Accordion multiple flush>
		<AccordionItem 
			tag="div"
			textFlushDefault="text-white"
			textFlushOpen="text-yellow-300 border-b-0 bg-stone-900"
			borderSharedClass="border-gray-200 dark:border-gray-50"
			borderBottomClass="border-b"
			paddingFlush="p-2"
		>
			<span slot="header">1 - Styles failing to load properly</span>
			<div class="bg-stone-900 p-4">
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
			</div>
		</AccordionItem>
		<AccordionItem 
			tag="div"
			textFlushDefault="text-white"
			textFlushOpen="text-yellow-300 border-b-0 bg-stone-900"
			borderSharedClass="border-gray-200 dark:border-gray-50"
			borderBottomClass="border-b"
			paddingFlush="p-2"
		>
			<span slot="header">2 - Styles not working in UI Builder</span>
			<div class="bg-stone-900 p-4">
				<P class="mb-2">Make sure you select the correct Theme.</P>
				<img alt="uibuildertheme" src={uibuildertheme} class="mb-6 xl:max-w-4xl max-w-full rounded-xl border-4" />
			</div>
		</AccordionItem>
		<AccordionItem 
			tag="div"
			textFlushDefault="text-white"
			textFlushOpen="text-yellow-300 border-b-0 bg-stone-900"
			borderSharedClass="border-gray-200 dark:border-gray-50"
			borderBottomClass="border-b"
			paddingFlush="p-2"
		>
			<span slot="header">3 - Inputs doesn't work, can't skip loading screen</span>
			<div class="bg-stone-900 p-4">
				<P class="mb-2">Assign <strong class="font-extrabold text-rose-400">Luna_InputSystem_Actions</strong> as the project wide input settings.</P>
				<img alt="InputSettingsNoProjectWideAsset" src={InputSettingsNoProjectWideAsset} class="mb-6 xl:max-w-4xl max-w-full rounded-xl border-4" />
			</div>
		</AccordionItem>
	</Accordion>
</div>
