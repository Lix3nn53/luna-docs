<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import tooltip from '$lib/img/docs/gallery/luna_tooltip.jpg';
	import tooltip_compare from '$lib/img/docs/components/tooltip_compare.jpg';
	import tooltip_inspector from '$lib/img/docs/components/tooltip_inspector.jpg';
	import input from '$lib/img/docs/gallery/luna_input.jpg';

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
	>Components/ Tooltip</Heading
>
<div class="p-4">
	<img alt="samples" src={tooltip} class="mb-6 max-w-2xl rounded-xl border-4" />
	<img alt="samples" src={tooltip_inspector} class="mb-6 max-w-md rounded-xl border-4" />
	<P>The tooltip itself is a simple component.</P>
	<P>
		However, we created an implementation of the Tooltip called <strong>DefaultTooltip</strong>.
		Controlling the DefaultTooltip is more complex to accommodate a wide range of scenarios.
	</P>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Attributes</Heading
	><Table class="rounded">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Attribute</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>FadeDelay</TableBodyCell>
				<TableBodyCell {tdClass}>Delay before starting to fade in or out.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>FadeUpdateFrequency</TableBodyCell>
				<TableBodyCell {tdClass}
					>The frequency (in milliseconds) for fade updates. Lower values result in faster fading.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Start Hidden</TableBodyCell>
				<TableBodyCell {tdClass}>Initial visibily.</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Tooltip Guide</Heading
	>

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>TooltipManipulator</Heading
	>
	<P
		>Add the TooltipManipulator to the VisualElements you want to display a tooltip for when they
		are hovered over or focused.</P
	>
	<CodeBlock
		language="csharp"
		code={`
var myTooltip = new Tooltip();
myTooltip.Add(new Label("This is a tooltip"));

var myElement = new VisualElement();
myElement.AddManipulator(new TooltipManipulator(myTooltip));`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P class="pt-4"
		>This will display the tooltip we created when myElement is hovered over or focused. As you can
		see, the Tooltip itself is very simple and may not suffice for more complex scenarios commonly
		encountered in games.</P
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Class Controls</Heading
	>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>Position</Heading
	>
	<P class="pb-2"
		>Apply these USS classes to the VisualElements that will display a tooltip when hovered over or
		focused to adjust the tooltip's position. Default value is top.</P
	><Table class="rounded">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>tooltip-left</TableBodyCell>
				<TableBodyCell {tdClass}>Position tooltip to the left of the VisualElement.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>tooltip-right</TableBodyCell>
				<TableBodyCell {tdClass}>Position tooltip to the right of the VisualElement.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>tooltip-bottom</TableBodyCell>
				<TableBodyCell {tdClass}>Position tooltip to the left of the VisualElement.</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>Follow Mouse</Heading
	><Table class="rounded">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>tooltip-follow</TableBodyCell>
				<TableBodyCell {tdClass}
					>The tooltip will position itself relative to the mouse instead of the VisualElement and
					will move along with the mouse.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>DefaultTooltip Guide</Heading
	>
	<P
		>This is where it gets complex. The Tooltip is a basic feature on its own, so we've provided a
		default tooltip to cover most use cases. You can refer to the TooltipDemo scene for setup
		guidance.</P
	>

	<img alt="samples" src={tooltip_compare} class="mb-6 max-w-2xl rounded-xl border-4" /><Heading
		tag="h2"
		class="my-4"
		customSize="text-xl font-bold md:text-2xl lg:text-3xl">InputIconDatabase</Heading
	>
	<P>Dictionaries of sprites for each control scheme.</P>
	<P
		>Icons used: <A
			color="text-sky-400 font-extrabold"
			href="https://www.kenney.nl/assets/input-prompts"
			target="_blank">https://www.kenney.nl/assets/input-prompts</A
		></P
	>
</div>
