<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import progressbar from '$lib/img/docs/components/progressbar.png';
	import progress_bars from '$lib/img/docs/gallery/luna_progress_bars.jpg';

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
	let tdClasss = 'px-6 py-2 whitespace-normal font-medium bg-stone-600';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Components/ Progress Bar</Heading
>
<div class="p-4">
	<img alt="samples" src={progress_bars} class="mb-6 max-w-2xl rounded-xl border-4" />
	<img alt="samples" src={progressbar} class="mb-6 max-w-md rounded-xl border-4" />
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Attributes</Heading
	><Table class="rounded">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Attribute</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Instant</TableBodyCell>
				<TableBodyCell {tdClass}
					>Next changes on Target Value and Target Indicator will be shown instantly.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Update Frequency</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>interval in ms</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Step</TableBodyCell>
				<TableBodyCell {tdClass}>How much length progress bar moves per update.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>First Delay</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Delay before the first bar starts to move. First bar can be main bar or indicator bar,
					depending on the change. If change is negative, main bar moves first followed by indicator
					bar. If change in positive, indicator bar moves first followed by main bar.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Second Delay</TableBodyCell>
				<TableBodyCell {tdClass}
					>Delay before the second bar starts to move. First bar can be main bar or indicator bar,
					depending on the change. If change is negative, main bar moves first followed by indicator
					bar. If change in positive, indicator bar moves first followed by main bar.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Target Value</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Target value to move towards for the main bar. A value be between 0 and 1.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Target Indicator</TableBodyCell>
				<TableBodyCell {tdClass}
					>Target value to move towards for the indicator bar. A value be between 0 and 1.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Title</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>Text to display on the bar.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Show Icon</TableBodyCell>
				<TableBodyCell {tdClass}>Show icon on left of the ProgressBar.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Icon Size</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>Width and height of the icon.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Icon Tint</TableBodyCell>
				<TableBodyCell {tdClass}>Image tint for the icon.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Vertical Line</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Make progress bar vertical instead of horizontal.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Color BG</TableBodyCell>
				<TableBodyCell {tdClass}>Background color.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Color Bar</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>Color of the main bar.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Color Indicator Positive</TableBodyCell>
				<TableBodyCell {tdClass}
					>Color of the indicator bar when the change is positive.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Color Indicator Negative</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>LColor of the indicator bar when the change is negative.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table>
</div>
