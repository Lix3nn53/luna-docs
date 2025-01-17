<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';
	import guide from '$lib/img/docs/components/guide.jpg';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Components/ Guide</Heading
>
<div class="p-4">
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Built-in Components</Heading
	>
	<P class="mb-2">
		Luna UI provides classes to improve and customize styles of built-in components.
	</P>
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Custom Components</Heading
	>
	<P class="mb-2">Custom components built from scratch.</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Using custom components</Heading
	>
	<P class="mb-2"
		>To add custom components in UI Builder: Select "Project" in Library section > unfold
		CupkekGames > drag & drop any component to Hierarchy section.</P
	>
	<img alt="samples" src={guide} class="mb-6 max-w-lg rounded-xl border-4" />
	<P class="mb-2">For more details, refer to the individual component's page.</P>
</div>
