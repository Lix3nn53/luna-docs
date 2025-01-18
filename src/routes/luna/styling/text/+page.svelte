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
	>Styling/ Text</Heading
>
<div class="p-4">
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Overriding Default Values</Heading
	>
	<P
		>Refer to <A color="text-sky-400 font-extrabold" href="/luna/styling/usssetup"
			>Styling/USS Setup</A
		> to learn how to apply these styles.</P
	>
	<CodeBlock
		language="css"
		code={`
:root {
  --font-black: url("/Packages/com.cupkekgames.uitk/Runtime/Fonts/rubik/Rubik-BlackSDF.asset");
  --font-black-italic: url("/Packages/com.cupkekgames.uitk/Runtime/Fonts/rubik/Rubik-BlackItalicSDF.asset");
  --font-bold: url("/Packages/com.cupkekgames.uitk/Runtime/Fonts/rubik/Rubik-BoldSDF.asset");
  --font-bold-italic: url("/Packages/com.cupkekgames.uitk/Runtime/Fonts/rubik/Rubik-BoldItalicSDF.asset");
  --font-light: url("/Packages/com.cupkekgames.uitk/Runtime/Fonts/rubik/Rubik-LightSDF.asset");
  --font-light-italic: url("/Packages/com.cupkekgames.uitk/Runtime/Fonts/rubik/Rubik-LightItalicSDF.asset");
  --font-medium: url("/Packages/com.cupkekgames.uitk/Runtime/Fonts/rubik/Rubik-MediumSDF.asset");
  --font-medium-italic: url("/Packages/com.cupkekgames.uitk/Runtime/Fonts/rubik/Rubik-MediumItalicSDF.asset");
}

:root,
Label {
  -unity-font-definition: var(--font-medium);
  -unity-font-style: normal;
  color: var(--color-neutral-50);
  font-size: var(--length-24);
}

.font-light {
  -unity-font-definition: var(--font-light);
}

.font-light-italic {
  -unity-font-definition: var(--font-light-italic);
}

.font-medium {
  -unity-font-definition: var(--font-medium);
}

.font-medium-italic {
  -unity-font-definition: var(--font-medium-italic);
}

.font-bold {
  -unity-font-definition: var(--font-bold);
}

.font-bold-italic {
  -unity-font-definition: var(--font-bold-italic);
}

.font-black {
  -unity-font-definition: var(--font-black);
}

.font-black-italic {
  -unity-font-definition: var(--font-black-italic);
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Utility Classes</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Text Color</Heading
	>
	<P><strong class="font-extrabold">Format:</strong> text-{'{'}color{'}'}-{'{'}tone{'}'}</P>
	<CodeBlock
		language="html"
		code={`
<engine:Label class="text-black" />
<engine:Label class="text-white" />
<engine:Label class="text-red-500" />
<engine:Label class="text-red-500-half" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Font Size</Heading
	>
	<Table class="rounded table-auto">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Properties</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>text-xs</TableBodyCell>
				<TableBodyCell {tdClass}>12px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>text-s</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>14x</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>text-md</TableBodyCell>
				<TableBodyCell {tdClass}>16px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>text-lg</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>18px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>text-xl</TableBodyCell>
				<TableBodyCell {tdClass}>20px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>text-2xl</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>24px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>text-3xl</TableBodyCell>
				<TableBodyCell {tdClass}>30px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>text-4xl</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>36px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>text-5xl</TableBodyCell>
				<TableBodyCell {tdClass}>48px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>text-6xl</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>60px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>text-7xl</TableBodyCell>
				<TableBodyCell {tdClass}>72px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>text-8xl</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>96px</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>text-9xl</TableBodyCell>
				<TableBodyCell {tdClass}>128px</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
</div>
