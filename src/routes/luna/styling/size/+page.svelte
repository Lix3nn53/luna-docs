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

	let tdheadClass = 'px-6 py-4 whitespace-normal font-medium bg-stone-800 text-stone-50';
	let tdrowClass = 'border-stone-500';
	let tdClass = 'px-6 py-2 whitespace-normal font-medium bg-stone-700';
	let tdClasss = 'px-6 py-2 whitespace-normal font-medium bg-stone-600 min-w-48';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Styling/ Size</Heading
>
<div class="p-4">
	Utilities for all things related to size.
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>USS variables</Heading
	>
	List of USS variables for length.
	<P><strong class="font-extrabold">Format:</strong> --length-{'{'}value{'}'}</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Values</Heading
	>
	<P class="mb-4"
		>0, 1, 2, 4, 6, 8, 10, 12, 14, 16, 20, 24, 28, 32, 36, 40, 44, 48, 56, 64, 80, 96, 112, 128,
		144, 160, 176, 192, 208, 224, 240, 256, 288, 320, 384, 448, 512, 640, 768, 896, 1024.</P
	>
	<P class="mb-4">Add "-neg" suffix for negative values.</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Usage</Heading
	>
	<CodeBlock
		language="css"
		code={`
.example {
    width: var(--length-16); /* 16px */
    height: var(--length-32); /* 32px */
    margin: var(--length-96); /* 96px */
    margin: var(--length-128-neg); /* -128px */
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Utility Classes</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Variants</Heading
	>
	<P
		>Utility classes has 2 versions; fixed pixel sizes and percentage. Here is a list of them, you
		will see how they are used in the next sections.</P
	>
	<CodeBlock
		language="html"
		code={`
<!-- Size in px -->
0, 1, 2, 4, 6, 8, 10, 12, 14, 16, 20, 24, 28, 32, 36, 40, 44, 48, 56, 64, 80, 96,
112, 128, 144, 160, 176, 192, 208, 224, 240, 256, 288, 320, 384

<!-- Size in percentage % -->
<!-- Increments of 5 -->
5p, 10p, 15p, 20p, 25p, 30p, 35p, 40p, 45p, 50p, 55p, 60p, 65p, 70p, 75p, 80p, 85p,
90p, 95p, 100p
<!-- Other -->
33p, 66p, full`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl">Size</Heading
	>
	<P>Sets both width and height to the same value.</P>
	<CodeBlock
		language="html"
		code={`
<engine:VisualElement class="size-128" />
<engine:VisualElement class="size-25p" />
<!-- 100p or full means 100% -->
<engine:VisualElement class="size-full" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Min/Max Size</Heading
	>
	<P>Sets both min/max width and height to the same value.</P>
	<CodeBlock
		language="html"
		code={`
<!-- Set min-width and min-height -->
<engine:VisualElement class="size-min-128" />
<engine:VisualElement class="size-min-50p" />
<!-- Set max-width and max-height -->
<engine:VisualElement class="size-max-128" />
<engine:VisualElement class="size-max-50p" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Width</Heading
	>
	<CodeBlock
		language="html"
		code={`
<!-- Set width -->
<engine:VisualElement class="w-128" />
<engine:VisualElement class="w-66p" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Min/Max Width</Heading
	>
	<CodeBlock
		language="html"
		code={`
<!-- Set min-width -->
<engine:VisualElement class="w-min-128" />
<!-- Set max-width -->
<engine:VisualElement class="w-max-512" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Height</Heading
	>
	<CodeBlock
		language="html"
		code={`
<!-- Set height -->
<engine:VisualElement class="h-128" />
<engine:VisualElement class="h-66p" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Min/Max Height</Heading
	>
	<CodeBlock
		language="html"
		code={`
<!-- Set min-height -->
<engine:VisualElement class="h-min-128" />
<!-- Set max-height -->
<engine:VisualElement class="h-max-512" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Margin</Heading
	>
	<CodeBlock
		language="html"
		code={`
<!-- Set margin -->
<engine:VisualElement class="m-16" />
<!-- Set margin top -->
<engine:VisualElement class="mt-16" />
<!-- Set margin bottom -->
<engine:VisualElement class="mb-16" />
<!-- Set margin right -->
<engine:VisualElement class="mr-16" />
<!-- Set margin left -->
<engine:VisualElement class="ml-16" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Padding</Heading
	>
	<CodeBlock
		language="html"
		code={`
<!-- Set padding -->
<engine:VisualElement class="p-16" />
<!-- Set padding top -->
<engine:VisualElement class="pt-16" />
<!-- Set padding bottom -->
<engine:VisualElement class="pb-16" />
<!-- Set padding right -->
<engine:VisualElement class="pr-16" />
<!-- Set padding left -->
<engine:VisualElement class="pl-16" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
