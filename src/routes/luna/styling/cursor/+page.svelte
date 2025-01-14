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

	import bracket_a_vertical from '$lib/img/docs/styling/cursor/bracket_a_vertical.png';
	import cursor_busy from '$lib/img/docs/styling/cursor/cursor_busy.png';
	import cursor_copy from '$lib/img/docs/styling/cursor/cursor_copy.png';
	import cursor_disabled from '$lib/img/docs/styling/cursor/cursor_disabled.png';
	import cursor_help from '$lib/img/docs/styling/cursor/cursor_help.png';
	import cursor_menu from '$lib/img/docs/styling/cursor/cursor_menu.png';
	import hand_small_closed from '$lib/img/docs/styling/cursor/hand_small_closed.png';
	import hand_small_open from '$lib/img/docs/styling/cursor/hand_small_open.png';
	import hand_small_point from '$lib/img/docs/styling/cursor/hand_small_point.png';
	import line_cross from '$lib/img/docs/styling/cursor/line_cross.png';
	import pointer_a from '$lib/img/docs/styling/cursor/pointer_a.png';
	import resize_a_cross from '$lib/img/docs/styling/cursor/resize_a_cross.png';
	import zoom_in from '$lib/img/docs/styling/cursor/zoom_in.png';
	import zoom_out from '$lib/img/docs/styling/cursor/zoom_out.png';

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
	>Styling/ Cursor</Heading
>
<div class="p-4">
	Change cursor icon when hovered.
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>USS Classes</Heading
	>
	<P><strong class="font-extrabold">Format:</strong> cursor-{'{'}value{'}'}</P>
	<CodeBlock
		language="html"
		code={`
<!-- Change cursor icon on hover -->
<engine:VisualElement class="cursor-move"/>`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<br />
	<Table class="rounded">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Icon</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>cursor-default</TableBodyCell>
				<TableBodyCell {tdClass}><img alt="pointer_a" src={pointer_a} class="w-12" /></TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>cursor-pointer</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					><img alt="hand_small_point" src={hand_small_point} class="w-12" /></TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>cursor-wait</TableBodyCell>
				<TableBodyCell {tdClass}
					><img alt="cursor_busy" src={cursor_busy} class="w-12" /></TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>cursor-text</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					><img alt="bracket_a_vertical" src={bracket_a_vertical} class="w-12" /></TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>cursor-move</TableBodyCell>
				<TableBodyCell {tdClass}
					><img alt="resize_a_cross" src={resize_a_cross} class="w-12" /></TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>cursor-help</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					><img alt="cursor_help" src={cursor_help} class="w-12" /></TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>cursor-not-allowed</TableBodyCell>
				<TableBodyCell {tdClass}
					><img alt="cursor_disabled" src={cursor_disabled} class="w-12" /></TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>cursor-context-menu</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					><img alt="cursor_menu" src={cursor_menu} class="w-12" /></TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>cursor-cell</TableBodyCell>
				<TableBodyCell {tdClass}
					><img alt="line_cross" src={line_cross} class="w-12" /></TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>cursor-copy</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					><img alt="cursor_copy" src={cursor_copy} class="w-12" /></TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>cursor-grab</TableBodyCell>
				<TableBodyCell {tdClass}
					><img alt="hand_small_open" src={hand_small_open} class="w-12" /></TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>cursor-grabbing</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					><img alt="hand_small_closed" src={hand_small_closed} class="w-12" /></TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>cursor-zoom-in</TableBodyCell>
				<TableBodyCell {tdClass}><img alt="zoom_in" src={zoom_in} class="w-12" /></TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>cursor-zoom-out</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					><img alt="zoom_out" src={zoom_out} class="w-12" /></TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>USS Variables</Heading
	>
	<CodeBlock
		language="css"
		code={`
--cursor-default
--cursor-pointer
--cursor-wait
--cursor-text
--cursor-move
--cursor-help
--cursor-not-allowed
--cursor-context-menu
--cursor-cell
--cursor-copy
--cursor-grab
--cursor-grabbing
--cursor-zoom-in
--cursor-zoom-out

/* Usage */
.example {
    cursor: var(--cursor-pointer);
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
