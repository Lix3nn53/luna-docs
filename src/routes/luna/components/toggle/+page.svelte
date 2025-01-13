<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';
	import sliderImg from '$lib/img/docs/components/slider.png';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Components/ Slider</Heading
>
<div class="p-4">
	<img alt="samples" src={sliderImg} class="mb-6 max-w-sm rounded-xl border-4" />
	<CodeBlock
		language="html"
		code={`
<engine:Slider 
 	label="Slider" 
	value="42" 
	high-value="100" 
	show-input-field="true" 
	inverted="false" 
	fill="true" 
	class="fill-pink dragger-teal focus-teal w-full" 
/>`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Colors</Heading
	>
	<P class="pt-4"
		>Refer to <A color="text-sky-400 font-extrabold" href="/luna/styling/colors">colors</A> to learn
		about available options.</P
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Fill Color</Heading
	>
	<P><strong class="font-extrabold">Format:</strong> fill-{'{'}color{'}'}</P>
	<CodeBlock
		language="html"
		code={`<engine:Slider class="fill-pink" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Dragger Color</Heading
	>
	<P><strong class="font-extrabold">Format:</strong> dragger-{'{'}color{'}'}</P>
	<CodeBlock
		language="html"
		code={`<engine:Slider class="dragger-teal" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Focus Color</Heading
	>
	<P><strong class="font-extrabold">Format:</strong> focus-{'{'}color{'}'}</P>
	<CodeBlock
		language="html"
		code={`<engine:Slider class="focus-teal" />`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
