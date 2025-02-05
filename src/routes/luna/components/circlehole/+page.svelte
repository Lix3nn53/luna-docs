<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import circle_hole from '$lib/img/docs/components/circle_hole.jpg';

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
	>Components/ Circle Hole Element</Heading
>
<div class="p-4">
	<P>Used in circle loading transition by tweening the radius.</P>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Attributes</Heading
	>
	<img alt="circle_hole" src={circle_hole} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" /><Table
		class="rounded"
	>
		<TableHead>
			<TableHeadCell class={tdheadClass}>Attribute</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Radius</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Radius of the circle.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Circle Segments</TableBodyCell>
				<TableBodyCell {tdClass}
					>Higher values result in smoother circle.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Fill Color</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>The fill color.</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
</div>
