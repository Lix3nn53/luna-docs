<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Alert } from 'flowbite-svelte';
	import dropdownImg from '$lib/img/docs/components/dropdown.png';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Components/ Dropdown</Heading
>
<div class="p-4">
	<img alt="samples" src={dropdownImg} class="mb-6 max-w-sm rounded-xl border-4" />

	<Alert border>
		<div class="flex flex-row">
			<i class="fa-solid fa-circle-info fa-2xl mr-4 mt-4"></i>
			<div>
				<P class="mb-4"
					>It is not possible to change color of the dropdown with just uss class. So Luna UI
					provides uss variables you can change.</P
				>
			</div>
		</div>
	</Alert>
	<CodeBlock
		language="css"
		code={`
/* USS Variables you can override */
:root {
  --color-dropdown-bg: var(--color-slate-600);
  --color-dropdown-hover: var(--color-slate-400);
  --color-dropdown-active: var(--color-red-400);
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P class="pt-4"
		>Refer to <A color="text-sky-400 font-extrabold" href="/luna/styling/colors">Styling/Colors</A> to
		learn about available options.</P
	>
</div>
