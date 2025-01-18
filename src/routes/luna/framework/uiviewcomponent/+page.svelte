<script>
	import { Heading, P, A, Mark, Secondary, Button, Hr } from 'flowbite-svelte';

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
	import uiviewcomponent from '$lib/img/docs/framework/uiviewcomponent.png';

	let tdheadClass = 'px-6 py-4 whitespace-normal font-medium bg-stone-800 text-stone-50';
	let tdrowClass = 'border-stone-200';
	let tdClass = 'px-6 py-4 whitespace-normal font-medium bg-stone-700 min-w-48';
	let tdClasss = 'px-6 py-4 whitespace-normal font-medium bg-stone-800 min-w-48';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>UIViewComponent</Heading
>
<div class="p-4">
	<P class="mb-4">
		Attach on a game object with <strong class="font-bold">UIDocument</strong> component. Creates an
		<strong class="font-bold">UIView</strong>
		for <strong class="font-bold">UIDocument.rootVisualElement</strong>.
	</P>
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Inspector View</Heading
	>
	<img alt="samples" src={uiviewcomponent} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Public Properties</Heading
	>
	<Table class="my-4 rounded border-4 border-stone-400 table-auto">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Name</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Type</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>UIView</TableBodyCell>
				<TableBodyCell {tdClass}>UIView</TableBodyCell>
				<TableBodyCell {tdClass}
					>The UIView created at Awake according to inspector settings.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>ParentElement</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>VisualElement</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>The VisualElement that serves as the parent for this UIView.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>LunaUIManager</TableBodyCell>
				<TableBodyCell {tdClass}
					><A color="text-sky-400 font-extrabold" href="/luna/framework/uimanager"
						>Luna UI Manager</A
					></TableBodyCell
				>
				<TableBodyCell {tdClass}
					>LunaUIManager tracks interactable visual elements, enabling mass activation or
					deactivation within a UIView. You can also set a blocking element to prevent interaction
					with other elements until it is clicked.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Fade</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					><A color="text-sky-400 font-extrabold" href="/luna/framework/fadeuielement"
						>FadeUIElement</A
					></TableBodyCell
				>
				<TableBodyCell tdClass={tdClasss}>Manage fade transitions of the UIView.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>UIDocument</TableBodyCell>
				<TableBodyCell {tdClass}>UIDocument</TableBodyCell>
				<TableBodyCell {tdClass}
					>UIDocument component attached to the same GameObject.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Public Methods</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>FadeOutThenDestroy</Heading
	>
	<P
		>This method uses the public Fade variable from the UIView to fade out. Once the fade-out
		transition is complete, it destroys the associated GameObject.</P
	>
	<CodeBlock
		language="csharp"
		code={`public void FadeOutThenDestroy()`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
