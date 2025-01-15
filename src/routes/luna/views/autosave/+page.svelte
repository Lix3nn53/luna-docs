<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import confirmationpopup_ex from '$lib/img/docs/components/confirmationpopup_ex.png';
	import autosavegif from '$lib/img/docs/views/autosave.gif';

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
	>Views/ Autosave Notification</Heading
>
<div class="p-4">
	<img
		alt="autosavegif"
		src={autosavegif}
		class="mb-6 max-w-2xl rounded-xl border-4"
	/>
	<P>An autosave notification that integrates with the <A color="text-sky-400 font-extrabold" href="/core/gamesavemanager">Game Save Manager</A> and utilizes the <A color="text-sky-400 font-extrabold" href="/luna/framework/examplemultipage">Radial Loading</A> component.</P>
</div>
