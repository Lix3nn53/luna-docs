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
	>Styling/ Colors</Heading
>
<div class="p-4">
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Default Colors</Heading
	>
	For full color palette, visit <A
		color="text-sky-400 font-extrabold"
		href="https://tailwindcss.com/docs/customizing-colors"
		target="_blank">Tailwind Colors</A
	>.
	<P class="my-4"
		>SLATE, GRAY, ZINC, NEUTRAL, STONE, RED, ORANGE, AMBER, YELLOW, LIME, GREEN, EMERALD, TEAL,
		CYAN, SKY, BLUE, INDIGO, VIOLET, PURPLE, FUCHSIA, PINK, and ROSE.</P
	>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Custom Color Slots</Heading
	>
	<P class="mb-4">BASE, PRIMARY, and SECONDARY.</P>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Color Tones</Heading
	>
	<P class="mb-4"
		>Each color has 11 tones, from light to dark: 50, 100, 200, 300, 400, 500, 600, 700, 800, 900,
		950.</P
	>
	<P class="mb-4">Each tone has a semi-transparent variant.</P><CodeBlock
		language="css"
		code={`
/* Color Red, Tone 500 */
.example {
	color: var(--color-red-500);
}
/* Color Red, Tone 500, Half Opacity */
.example {
	color: var(--color-red-500-half);
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>USS Variables</Heading
	>
	<P class="mb-4">You can use uss variables in your style sheets.</P>
	<CodeBlock
		language="css"
		code={`
.example {
  background-color: var(--color-primary-50);
  border-color: var(--color-slate-900);
  color: var(--color-lime-900);
  -unity-background-image-tint-color: var(--color-gray-500);
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>USS Classes</Heading
	>
	<P class="mb-4">Or you can use uss classes to directly color your visual elements.</P>
	<P class="mb-4"
		>In addition to colors listed above, the classes also include 'transparent', 'black', and
		'white'.</P
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Background Color</Heading
	>
	<P><strong class="font-extrabold">Format:</strong> bg-{'{'}color{'}'}-{'{'}tone{'}'}</P>
	<CodeBlock
		language="html"
		code={`
<engine:VisualElement class="bg-transparent" />
<engine:VisualElement class="bg-red-500" />
<engine:VisualElement class="bg-red-500-half" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
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
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
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
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Image Tint Color</Heading
	>
	<P><strong class="font-extrabold">Format:</strong> tint-{'{'}color{'}'}-{'{'}tone{'}'}</P>
	<CodeBlock
		language="html"
		code={`
<engine:VisualElement class="tint-white" />
<engine:VisualElement class="tint-red-500" />
<engine:VisualElement class="tint-red-500-half" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>UIColor Class</Heading
	>
	<P>Allows you to easily apply uss classes listed above to VisualElements from code.</P>
	<CodeBlock
		language="csharp"
		code={`
UIColor uiColor = new UIColor(UIColorName.Purple, UIColorValue.V_400);

// Set background color
visualElement.AddToClassList(uiColor.GetUssClassBG());
// Set border color
visualElement.AddToClassList(uiColor.GetUssClassBorder());
// Set text color
visualElement.AddToClassList(uiColor.GetUssClassText());
// Set image tink color
visualElement.AddToClassList(uiColor.GetUssClassImageTint());`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
