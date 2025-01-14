<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import tabs_h from '$lib/img/docs/components/tabs_h.png';
	import tabs_v from '$lib/img/docs/components/tabs_v.png';
	import settings from '$lib/img/docs/views/settings.jpg';
	import tabs_inspector from '$lib/img/docs/components/tabs_inspector.jpg';
	import tabs_usage_1 from '$lib/img/docs/components/tabs_usage_1.png';
	import tabs_usage_2 from '$lib/img/docs/components/tabs_usage_2.png';
	import tabs_usage_3 from '$lib/img/docs/components/tabs_usage_3.png';
	import tabs_usage_4 from '$lib/img/docs/components/tabs_usage_4.png';
	import tabs_layout from '$lib/img/docs/components/tabs_layout.png';

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
	>Components/ Tab View</Heading
>
<div class="p-4">
	<img alt="tabs_h" src={tabs_h} class="mb-6 max-w-2xl rounded-xl border-4" />
	<img alt="tabs_v" src={tabs_v} class="mb-6 max-w-64 rounded-xl border-4" />
	<img alt="settings" src={settings} class="mb-6 max-w-2xl rounded-xl border-4" />
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Unity has built-in TabView, why make a new one?</Heading
	>
	<P
		>The built-in TabView has a problem, the buttons to change tabs are un-interactable
		VisualElements instead of interactable buttons.</P
	>
	<P>Plus, we have added InputPrompts to navigate between tabs on gamepads.</P>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Attributes</Heading
	>
	<img alt="tabs_inspector" src={tabs_inspector} class="mb-6 max-w-2xl rounded-xl border-4" /><Table
		class="rounded"
	>
		<TableHead>
			<TableHeadCell class={tdheadClass}>Attribute</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Horizontal</TableBodyCell>
				<TableBodyCell {tdClass}>Horizontal if true, vertical otherwise.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Button Color</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>Inactive buttons' color.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Button Color Selected</TableBodyCell>
				<TableBodyCell {tdClass}>Active button's color.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Active Tab</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>Index of active tab.</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Usage</Heading
	>
	<img alt="tabs_layout" src={tabs_layout} class="mb-6 max-w-64 rounded-xl border-4" />
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>1 - Drag and drop custom TabView to your Hierarchy</Heading
	>
	<img alt="tabs_usage_1" src={tabs_usage_1} class="mb-6 max-w-64 rounded-xl border-4" />
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>2 - Drag and drop default Tab to the TabView</Heading
	>
	<img alt="tabs_usage_2" src={tabs_usage_2} class="mb-6 max-w-64 rounded-xl border-4" />
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>3 - Configure Tab and add content inside it</Heading
	>
	<img alt="tabs_usage_3" src={tabs_usage_3} class="mb-6 max-w-64 rounded-xl border-4" />
	<img alt="tabs_usage_4" src={tabs_usage_4} class="mb-6 max-w-64 rounded-xl border-4" />
</div>
