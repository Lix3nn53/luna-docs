<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Alert } from 'flowbite-svelte';
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
	<img alt="samples" src={listImg} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<CodeBlock
		language="html"
		code={`
<engine:ListView name="ListPrimary" fixed-item-height="100" class="primary" />
<engine:ListView name="ListPurple" fixed-item-height="100" class="purple" />
<engine:ListView name="ListDefault" fixed-item-height="100" />

<engine:ScrollView class="primary">
<engine:ScrollView class="red">

<!-- Ghost -->
<engine:ListView class="red ghost">
<engine:ScrollView class="red ghost">`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Alert border class="my-4">
		<div class="flex flex-row">
			<i class="fa-solid fa-circle-info fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-2">
					This page shows visual styling examples for ListView components. For functional keyboard navigation and focus management, refer to <A color="text-sky-400 font-extrabold" href="/luna/utility/listviewwrapper">ListViewWrapper</A>.
				</P>
			</div>
		</div>
	</Alert>
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
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Ghost</Heading
	>
	<P
		>Makes the background transparent.</P
	>
	<CodeBlock
		language="html"
		code={`
<!-- Ghost -->
<engine:ListView class="red ghost">
<engine:ScrollView class="red ghost">`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
