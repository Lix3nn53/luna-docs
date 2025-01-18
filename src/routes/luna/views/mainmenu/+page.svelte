<script>
	import {
		Heading,
		P,
		A,
		Mark,
		Secondary,
		GradientButton,
		Hr,
		Li,
		List,
		Alert
	} from 'flowbite-svelte';
	import mainmenu from '$lib/img/docs/views/mainmenu.jpg';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';

	import {
		Table,
		TableBody,
		TableBodyCell,
		TableBodyRow,
		TableHead,
		TableHeadCell
	} from 'flowbite-svelte';

	let tdheadClass = 'px-6 py-4 whitespace-normal font-medium bg-stone-800 text-stone-50';
	let tdrowClass = 'border-stone-500';
	let tdClass = 'px-6 py-2 whitespace-normal font-medium bg-stone-700';
	let tdClasss = 'px-6 py-2 whitespace-normal font-medium bg-stone-600 min-w-48';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Views/ Main Menu</Heading
>
<div class="p-4">
	<img alt="mainmenu" src={mainmenu} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<P
		>An example implementation that you can use directly or as a starting point. You can refer to
		the demo game samples to see it in action or see the implementation details.</P
	>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>MainMenuView{'<TSaveData>'}</Heading
	>
	<P>Base class with buttons:</P>
	<List tag="ul" class="space-y-1 py-2">
		<Li>Continue</Li>
		<Li>Load</Li>
		<Li>New Game</Li>
		<Li>Settings</Li>
		<Li>Credits</Li>
		<Li>Quit</Li>
	</List>
	<Alert border>
		<div class="flex flex-row">
			<i class="fa-solid fa-circle-info fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-4"
					>The Continue and Load buttons are enabled or disabled automatically based on the presence
					of a save file, in coordination with the GameSaveManager.</P
				>
			</div>
		</div>
	</Alert>
</div>
