<script>
	import { Heading, P, A, List, Li } from 'flowbite-svelte';

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

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">Samples/ Asset Sources</Heading
>
<div class="p-4">
	<Table class="rounded table-auto">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Credits</TableHeadCell>
			<TableHeadCell class={tdheadClass}>License</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Assets In Tool</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Assets In Samples</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}><A color="text-sky-400 font-extrabold" href="https://www.kenney.nl" target="_blank">Kenney.nl</A></TableBodyCell>
				<TableBodyCell {tdClass}><A color="text-sky-400 font-extrabold" href="https://creativecommons.org/publicdomain/zero/1.0/" target="_blank">CC0 1.0 Universal</A></TableBodyCell>
				<TableBodyCell {tdClass}>Icons, cursors, and input prompts</TableBodyCell>
				<TableBodyCell {tdClass}>Sound effects such as button clicks</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}><A color="text-sky-400 font-extrabold" href="https://kaylousberg.itch.io/kaykit-adventurers" target="_blank">Kaylousberg</A></TableBodyCell>
				<TableBodyCell {tdClass}><A color="text-sky-400 font-extrabold" href="https://creativecommons.org/publicdomain/zero/1.0/" target="_blank">CC0 1.0 Universal</A></TableBodyCell>
				<TableBodyCell {tdClass}>NONE</TableBodyCell>
				<TableBodyCell {tdClass}>Avatar sprites</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}><A color="text-sky-400 font-extrabold" href="https://ravenmore.itch.io/fantasy-icon-pack" target="_blank">Ravenmore</A></TableBodyCell>
				<TableBodyCell {tdClass}><A color="text-sky-400 font-extrabold" href="https://creativecommons.org/publicdomain/zero/1.0/" target="_blank">CC0 1.0 Universal</A></TableBodyCell>
				<TableBodyCell {tdClass}>NONE</TableBodyCell>
				<TableBodyCell {tdClass}>Item icons</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
</div>
