<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';
	import radiobuttongroupImg from '$lib/img/docs/components/radiobuttongroup.png';

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
	>Components/ RadioButtonGroup</Heading
>
<div class="p-4">
	<img alt="samples" src={radiobuttongroupImg} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<CodeBlock
		language="html"
		code={`
<!-- Default -->
<engine:RadioButtonGroup choices="a,b,c,d" label="Default" />
<!-- Horizontal -->
<engine:RadioButtonGroup choices="a,b,c,d" label="Horizontal" class="radio-horizontal" />
<!-- Horizontal & Red -->
<engine:RadioButtonGroup choices="a,b,c,d" label="Horizontal Red" class="radio-horizontal red" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Horizontal</Heading
	>
	<Table class="rounded">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>horizontal</TableBodyCell>
				<TableBodyCell {tdClass}>flex-direction: row;</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Colors</Heading
	>
	<P>To change the color of a toggle, add the color name as a class without a value.</P>
	<CodeBlock
		language="html"
		code={`<engine:RadioButtonGroup choices="a,b,c,d" label="Horizontal" class="radio-horizontal" />`}
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
