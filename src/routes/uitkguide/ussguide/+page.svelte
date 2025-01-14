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
		Button
	} from 'flowbite-svelte';

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
	>UITK/ USS Guide</Heading
>
<div class="p-4">
	<P
		>Unity Style Sheet (USS) files are text files inspired by Cascading Style Sheets (CSS) from
		HTML. They are primarily used to define the appearance and styles of UI elements.</P
	>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Unity Documentation</Heading
	>
	<P class="mb-4">If you are unfamiliar with the basics, you can refer to Unity's documentation.</P>
	<Button
		outline
		color="yellow"
		href="https://docs.unity3d.com/Manual/UI-system-compare.html"
		target="_blank"
	>
		Unity USS Documentation
		<i class="fa-solid fa-up-right-from-square ms-2 flex items-center"></i>
	</Button>
</div>
