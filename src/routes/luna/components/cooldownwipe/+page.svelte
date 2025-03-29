<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import circle_hole from '$lib/img/docs/components/cooldownwipe.webp';

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
	>Components/ CooldownWipe</Heading
>
<div class="p-4">
	<P>Useful for showing cooldown of skills or duration of status effects/buffs over their icons.</P>
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
				<TableBodyCell tdClass={tdClasss}>Progress</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Controls the progress of the wipe animation (0 to 1).</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Fill Color</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>Sets the color that fills the element.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Segment Amount</TableBodyCell>
				<TableBodyCell {tdClass}
					>Number of segments used to draw the wipe element. Higher values create a smoother appearance.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Reverse Binding</TableBodyCell>
				<TableBodyCell {tdClass}
					>When true, reverses the direction of the wipe animation.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Line Width</TableBodyCell>
				<TableBodyCell {tdClass}
					>Thickness of the line in pixels.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Line Color</TableBodyCell>
				<TableBodyCell {tdClass}
					>Color of the line.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table>
</div>
