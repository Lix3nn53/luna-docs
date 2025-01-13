<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';
	import listImg from '$lib/img/docs/components/list.png';

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

	let tdheadClass = 'px-6 py-2 whitespace-normal font-medium bg-stone-800 text-stone-50';
	let tdrowClass = 'border-stone-500';
	let tdClass = 'px-6 py-2 whitespace-normal font-medium bg-stone-600 min-w-48';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Components/ List & ScrollView</Heading
>
<div class="p-4">
	<img alt="samples" src={listImg} class="mb-6 max-w-2xl rounded-xl border-4" />
	<CodeBlock
		language="html"
		code={`
<engine:ListView name="ListPrimary" fixed-item-height="100" class="primary" />
<engine:ListView name="ListRed" fixed-item-height="100" class="red" />
<engine:ListView name="ListPurple" fixed-item-height="100" class="purple" />
<engine:ListView name="ListDefault" fixed-item-height="100" />

<engine:ScrollView class="primary">
<engine:ScrollView class="red">`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Colors</Heading
	>
	<P
		>To change the color of a ListView or ScrollView, add the color name as a class without a value.</P
	>
	<CodeBlock
		language="html"
		code={`
<engine:ListView class="purple" />
<engine:ScrollView class="purple" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P class="pt-4"
		>Refer to <A color="text-sky-400 font-extrabold" href="/luna/styling/colors">colors</A> to learn
		about available options.</P
	>
</div>
