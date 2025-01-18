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
	import setup_theme from '$lib/img/docs/styling/setup_theme.jpg';
	import setup_panel_settings from '$lib/img/docs/styling/setup_panel_settings.jpg';

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
	let tdClass = 'px-6 py-2 whitespace-normal font-medium bg-stone-700';
	let tdClasss = 'px-6 py-2 whitespace-normal font-medium bg-stone-600 min-w-48';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Styling/ Border</Heading
>
<div class="p-4">
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Example</Heading
	>
	<CodeBlock
		language="html"
		code={`
<!-- Set border width, radius and color -->
<engine:VisualElement class="border-8 rounded-lg border-red-400"/>`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Border Width</Heading
	>
	<P><strong class="font-extrabold">Format:</strong> border-{'{'}value{'}'}</P>
	<Table class="rounded table-auto">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Properties</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>border-0</TableBodyCell>
				<TableBodyCell {tdClass}>border-width: 0</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>border-1</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>border-width: 1px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>border-2</TableBodyCell>
				<TableBodyCell {tdClass}>border-width: 2px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>border-4</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>border-width: 4px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>border-8</TableBodyCell>
				<TableBodyCell {tdClass}>border-width: 8px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>border-12</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>border-width: 12px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>border-16</TableBodyCell>
				<TableBodyCell {tdClass}>border-width: 16px</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Border Radius</Heading
	>
	<P><strong class="font-extrabold">Format:</strong> rounded-{'{'}value{'}'}</P>
	<Table class="rounded table-auto">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Properties</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>rounded-none</TableBodyCell>
				<TableBodyCell {tdClass}>border-radius: 0</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>rounded-sm</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>border-radius: 2px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>rounded</TableBodyCell>
				<TableBodyCell {tdClass}>border-radius: 4px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>rounded-md</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>border-radius: 6px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>rounded-lg</TableBodyCell>
				<TableBodyCell {tdClass}>border-radius: 8px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>rounded-xl</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>border-radius: 12px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>rounded-2xl</TableBodyCell>
				<TableBodyCell {tdClass}>border-radius: 16px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>rounded-3xl</TableBodyCell>
				<TableBodyCell {tdClass}>border-radius: 24px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>rounded-full</TableBodyCell>
				<TableBodyCell {tdClass}>border-radius: 9999px</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Border Color</Heading
	>
	<P><strong class="font-extrabold">Format:</strong> border-{'{'}color{'}'}-{'{'}tone{'}'}</P>
	<CodeBlock
		language="html"
		code={`
<engine:VisualElement class="border-purple-700" />
<engine:VisualElement class="border-red-500" />
<engine:VisualElement class="border-red-500-half" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
