<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import radial_loading from '$lib/img/docs/components/radial_loading.jpg';
	import radial_loading_inspector from '$lib/img/docs/components/radial_loading_inspector.jpg';

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
	>Components/ Radial Loading</Heading
>
<div class="p-4">
	<img alt="samples" src={radial_loading} class="mb-6 max-w-2xl rounded-xl border-4" />
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Attributes</Heading
	>
	<img
		alt="samples"
		src={radial_loading_inspector}
		class="mb-6 max-w-md rounded-xl border-4"
	/><Table class="rounded">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Attribute</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Arc Size</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Next changes on Target Value and Target Indicator will be shown instantly.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Line Width</TableBodyCell>
				<TableBodyCell {tdClass}>Width of the line that draws the circle.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Update Frequency</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>interval in ms</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Step</TableBodyCell>
				<TableBodyCell {tdClass}>How much length progress bar moves per update.</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
</div>
