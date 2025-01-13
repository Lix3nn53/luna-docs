<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';
	import toggleImg from '$lib/img/docs/components/toggle.png';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Components/ Toggle</Heading
>
<div class="p-4">
	<img alt="samples" src={toggleImg} class="mb-6 max-w-sm rounded-xl border-4" />
	<CodeBlock
		language="html"
		code={`
<engine:Toggle label="Toggle" />
<engine:Toggle label="Toggle" class="yellow" />
<engine:Toggle label="Toggle" class="red"`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Colors</Heading
	>
	<P>To change the color of a toggle, add the color name as a class without a value.</P>
	<CodeBlock
		language="html"
		code={`<engine:Toggle label="Toggle" class="sky" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P class="pt-4"
		>Refer to <A color="text-sky-400 font-extrabold" href="/luna/styling/colors">colors</A> to learn
		about available options.</P
	>
</div>
