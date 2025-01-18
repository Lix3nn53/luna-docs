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
	>Styling/ Layout</Heading
>
Utility classes to provide an easy way to adjust the layout of the elements.
<div class="p-4">
	Utilities for all things related to size.
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Position</Heading
	>
	<CodeBlock
		language="html"
		code={`
<!-- Position Relative -->
<engine:VisualElement class="relative" />
<!-- Position Absolute-->
<engine:VisualElement class="absolute" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Top / Right / Bottom / Left</Heading
	>
	<P
		><strong class="font-extrabold">Format:</strong> top-{'{'}value{'}'} / right-{'{'}value{'}'} / bottom-{'{'}value{'}'}
		/ left-{'{'}value{'}'}</P
	>
	<P class="my-4"
		>Uses same length variables mentioned at <A
			color="text-sky-400 font-extrabold"
			href="/luna/styling/size">Styling/Size</A
		>.</P
	>
	<CodeBlock
		language="html"
		code={`
<!-- set left -->
<engine:VisualElement class="left-4" />
<!-- set right-->
<engine:VisualElement class="right-10p" />
<!-- set top -->
<engine:VisualElement class="top-full" />
<!-- set bottom -->
<engine:VisualElement class="bottom-20-neg" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Flex</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Flex Direction</Heading
	>
	<CodeBlock
		language="html"
		code={`
<!-- flex-direction: row -->
<engine:VisualElement class="flex-row" />
<!-- flex-direction: row-reverse -->
<engine:VisualElement class="flex-row-reverse" />
<!-- flex-direction: column-->
<engine:VisualElement class="flex-col" />
<!-- flex-direction: column-reverse -->
<engine:VisualElement class="flex-col-reverse" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Flex Grow & Shrink</Heading
	>
	<P
		><strong class="font-extrabold">Values:</strong> 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14,
		15.</P
	>
	<CodeBlock
		language="html"
		code={`
<!-- flex-grow -->
<engine:VisualElement class="grow-4" />
<engine:VisualElement class="grow-15" />
<!-- flex-shrink -->
<engine:VisualElement class="shrink-0" />
<engine:VisualElement class="shrink-9" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Align Items</Heading
	>
	<Table class="rounded table-auto">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Properties</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>items-auto</TableBodyCell>
				<TableBodyCell {tdClass}>align-items: auto</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>items-start</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>align-items: flex-start</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>items-end</TableBodyCell>
				<TableBodyCell {tdClass}>align-items: flex-end</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>items-center</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>align-items: center</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>items-stretch</TableBodyCell>
				<TableBodyCell {tdClass}>align-items: stretch</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Justify Content</Heading
	>
	<Table class="rounded table-auto">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Properties</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>justify-start</TableBodyCell>
				<TableBodyCell {tdClass}>justify-content: flex-start</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>justify-center</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>justify-content: center</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>justify-end</TableBodyCell>
				<TableBodyCell {tdClass}>justify-content: flex-end</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>justify-between</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>justify-content: space-between</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>justify-around</TableBodyCell>
				<TableBodyCell {tdClass}>justify-content: space-around</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>justify-around</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>justify-content: space-around</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Align Self</Heading
	>
	<Table class="rounded table-auto">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Properties</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>self-auto</TableBodyCell>
				<TableBodyCell {tdClass}>align-self: auto</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>self-start</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>align-self: flex-start</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>self-end</TableBodyCell>
				<TableBodyCell {tdClass}>align-self: flex-end</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>self-center</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>align-self: center</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>self-stretch</TableBodyCell>
				<TableBodyCell {tdClass}>align-self: stretch</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Align Content</Heading
	>
	<Table class="rounded table-auto">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Properties</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>align-auto</TableBodyCell>
				<TableBodyCell {tdClass}>align-content: auto</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>align-start</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>align-content: flex-start</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>align-end</TableBodyCell>
				<TableBodyCell {tdClass}>align-content: flex-end</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>align-center</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>align-content: center</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>align-stretch</TableBodyCell>
				<TableBodyCell {tdClass}>align-content: stretch</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
</div>
