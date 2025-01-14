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
	>Styling/ USS Setup</Heading
>
<div class="p-4">
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Setting up a theme file</Heading
	>
	<P class="mb-4">As always, you can refer to Game sample for an example setup.</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>1 - Theme File</Heading
	>
	<P class="mb-4"
		>If you want to be able to use LunaUI's style files along with your custom styles, you need to
		inherit from "CupkekGamesMainTheme".</P
	>
	<img alt="setup_theme" src={setup_theme} class="mb-6 max-w-lg rounded-xl border-4" />
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>2 - Panel Settings</Heading
	>
	<P class="mb-4">Make sure your panel settings are using the correct Theme Style Sheet.</P>
	<img
		alt="setup_panel_settings"
		src={setup_panel_settings}
		class="mb-6 max-w-lg rounded-xl border-4"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>3 - Overriding or expanding global styles</Heading
	>
	<P class="mb-4"
		>As shown in the image in step 1, colors, fonts, and dropdown style sheets have been added.
		These style sheets override the styles from the CupkekGamesMainTheme.</P
	>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>Text & font</Heading
	>
	<P class="mb-4"
		>For example, to style text and fonts, refer to <A
			color="text-sky-400 font-extrabold"
			href="/luna/styling/text">Text</A
		>.</P
	>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>Override dropdown colors</Heading
	><CodeBlock
		language="css"
		code={`
:root {
	--color-dropdown-bg: var(--color-slate-600);
	--color-dropdown-hover: var(--color-slate-400);
	--color-dropdown-active: var(--color-primary-400);
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>Define the base, primary and secondary colors</Heading
	><CodeBlock
		language="css"
		code={`
:root {
	--color-base-50: #f8fafc;
	--color-base-100: #f1f5f9;
	--color-base-200: #e2e8f0;
	--color-base-300: #cbd5e1;
	--color-base-400: #94a3b8;
	--color-base-500: #64748b;
	--color-base-600: #475569;
	--color-base-700: #334155;
	--color-base-800: #1e293b;
	--color-base-900: #0f172a;
	--color-base-950: #020617;

	--color-primary-50: #faf5ff;
	--color-primary-100: #f3e8ff;
	--color-primary-200: #e9d5ff;
	--color-primary-300: #d8b4fe;
	--color-primary-400: #c084fc;
	--color-primary-500: #a855f7;
	--color-primary-600: #9333ea;
	--color-primary-700: #7e22ce;
	--color-primary-800: #6b21a8;
	--color-primary-900: #581c87;
	--color-primary-950: #3b0764;

	--color-secondary-50: #f0fdfa;
	--color-secondary-100: #ccfbf1;
	--color-secondary-200: #99f6e4;
	--color-secondary-300: #5eead4;
	--color-secondary-400: #2dd4bf;
	--color-secondary-500: #14b8a6;
	--color-secondary-600: #0d9488;
	--color-secondary-700: #0f766e;
	--color-secondary-800: #115e59;
	--color-secondary-900: #134e4a;
	--color-secondary-950: #042f2e;
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
