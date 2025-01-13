<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';
	import buttonImg from '$lib/img/docs/components/button.png';

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
	let tdClass = 'px-6 py-2 whitespace-normal font-medium bg-stone-600';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Components/ Button</Heading
>
<div class="p-4">
	<img alt="samples" src={buttonImg} class="mb-6 max-w-2xl rounded-xl border-4" />
	<CodeBlock
		language="html"
		code={`
<!-- Apply Style -->
<engine:Button class="btn" />
<!-- With Size -->
<engine:Button class="btn btn-lg" />
<!-- With Color -->
<engine:Button class="btn red" />
<!-- With Size and Color -->
<engine:Button class="btn btn-xl violet" />
<!-- GHOST -->
<engine:Button class="btn btn-xl violet ghost" />
<!-- MASKED -->
<engine:Button class="btn btn-xl violet masked" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Size</Heading
	>
	<Table class="rounded">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>btn-sm</TableBodyCell>
				<TableBodyCell {tdClass}>Small</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>btn-lg</TableBodyCell>
				<TableBodyCell {tdClass}>Large</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>btn-xl</TableBodyCell>
				<TableBodyCell {tdClass}>xLarge</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Color</Heading
	>
	<P>To change the color of a button, add the color name as a class without a value.</P>
	<CodeBlock
		language="html"
		code={`<engine:Button class="btn teal" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P class="pt-4"
		>Refer to <A color="text-sky-400 font-extrabold" href="/luna/styling/colors">colors</A> to learn
		about available options.</P
	>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Special</Heading
	>
	<Table class="rounded">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>ghost</TableBodyCell>
				<TableBodyCell {tdClass}
					>A class which gives the button a transparent background. Upon hover and focus states, the
					background changes to a semi-transparent black color and the text color changes to be
					whichever color class the button was given.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>masked</TableBodyCell>
				<TableBodyCell {tdClass}
					>A class which gives the button a transparent background. Upon hover and focus states, the
					background changes to whichever color class the button was given and text color remains
					the same.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table>
</div>
