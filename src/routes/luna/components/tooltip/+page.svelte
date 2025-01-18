<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import tooltip from '$lib/img/docs/gallery/luna_tooltip.jpg';
	import tooltip_compare from '$lib/img/docs/components/tooltip_compare.jpg';
	import tooltip_inspector from '$lib/img/docs/components/tooltip_inspector.jpg';
	import default_tooltip_inspector from '$lib/img/docs/components/default_tooltip_inspector.jpg';
	import default_tooltip_setup from '$lib/img/docs/components/default_tooltip_setup.jpg';

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
	let tdClass = 'px-6 py-2 whitespace-normal font-medium bg-stone-600 min-w-48';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Components/ Tooltip</Heading
>
<div class="p-4">
	<img alt="tooltip" src={tooltip} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<p>The tooltip is a straightforward component.</p>
	<p>
			For more complex needs, we provide an implementation called <strong>DefaultTooltip</strong>. It is designed to handle a wide range of scenarios.
	</p>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Attributes</Heading
	>
	<img alt="samples" src={tooltip_inspector} class="mb-6 max-w-md rounded-xl border-4" /><Table
		class="rounded"
	>
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

	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
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
		see, the Tooltip itself is very simple.</P
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Class Controls</Heading
	>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>Position</Heading
	>
	<P class="pb-2"
		>Apply these USS classes to the VisualElements that will display a tooltip when hovered over or
		focused to adjust the tooltip's position. Default value is top.</P
	><Table class="rounded table-auto">
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
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>Follow Mouse</Heading
	><Table class="rounded table-auto">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Class</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>tooltip-follow</TableBodyCell>
				<TableBodyCell {tdClass}
					>The tooltip will position itself relative to the mouse instead of the VisualElement and
					will move along with the mouse. Position class controls still apply.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>DefaultTooltip Guide</Heading
	>
	<img alt="samples" src={tooltip_compare} class="mb-4 xl:max-w-xl max-w-full rounded-xl border-4" />
	<P class="pb-4"
		>To support more complex scenarios commonly
		encountered in games, we've provided a default implementation to cover most use cases.</P
	>
	<P class="pb-4"
		>DefaultTooltip is not an extension of Tooltip; it is an extension of TooltipManipulator. It
		creates and controls a Tooltip with customizable slots and the ability to display multiple columns
		simultaneously.</P
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Setup</Heading
	>
	<P class="pb-4"
		>You can just copy the setup from demo Game samples. All you need is to create a document with
		Tooltip component named DefaultTooltip.</P
	>
	<img alt="samples" src={default_tooltip_setup} class="mb-6 max-w-md rounded-xl border-4" />
	<img alt="samples" src={default_tooltip_inspector} class="mb-6 max-w-md rounded-xl border-4" />
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>DefaultTooltipManipulator</Heading
	>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>Constructor</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
// Create manipulator with multiple columns, as demonstrated in the item comparison tooltip example above.
public DefaultTooltipManipulator(GameObject parent, DefaultTooltip tooltip, List<DefaultTooltipContainerSetup> setups);
// Create manipulator with one column
var manipulator = public DefaultTooltipManipulator(GameObject parent, DefaultTooltip tooltip);
manipulator.SetSetup(setup);`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<br /><Table class="rounded table-auto">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Name</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Type</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>parent</TableBodyCell>
				<TableBodyCell {tdClass}>GameObject</TableBodyCell>
				<TableBodyCell {tdClass}
					>The tooltip will automatically close when this GameObject is disabled.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>tooltip</TableBodyCell>
				<TableBodyCell {tdClass}>DefaultTooltip</TableBodyCell>
				<TableBodyCell {tdClass}>Referance to the tooltip to control.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>setup</TableBodyCell>
				<TableBodyCell {tdClass}>DefaultTooltipContainerSetup</TableBodyCell>
				<TableBodyCell {tdClass}>Container setup for a column. See below for details.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table><br />
	<Heading tag="h4" class="mb-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>DefaultTooltipContainerSetup</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
// Constructor of DefaultTooltipContainerSetup
public DefaultTooltipContainerSetup(
	VisualElement image, 
	VisualElement title, 
	VisualElement body, 
	VisualElement bottom,
	UIColor colorBackground = null, 
	UIColor colorBorder = null, 
	int maxWidth = 512
)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/><br /><Table class="rounded table-auto">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Name</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Type</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>image</TableBodyCell>
				<TableBodyCell {tdClass}>VisualElement</TableBodyCell>
				<TableBodyCell {tdClass}>VisualElement to place in the image slot.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>title</TableBodyCell>
				<TableBodyCell {tdClass}>VisualElement</TableBodyCell>
				<TableBodyCell {tdClass}>VisualElement to place in the title slot.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>body</TableBodyCell>
				<TableBodyCell {tdClass}>VisualElement</TableBodyCell>
				<TableBodyCell {tdClass}>VisualElement to place in the body slot.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>bottom</TableBodyCell>
				<TableBodyCell {tdClass}>VisualElement</TableBodyCell>
				<TableBodyCell {tdClass}
					>VisualElement to place in the bottom slot. Use this slot if you don't want any prior
					layout.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>colorBackground</TableBodyCell>
				<TableBodyCell {tdClass}>UIColor</TableBodyCell>
				<TableBodyCell {tdClass}>Change tooltip container's background color.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>colorBorder</TableBodyCell>
				<TableBodyCell {tdClass}>UIColor</TableBodyCell>
				<TableBodyCell {tdClass}>Change tooltip container's border color.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>maxWidth</TableBodyCell>
				<TableBodyCell {tdClass}>int</TableBodyCell>
				<TableBodyCell {tdClass}>Change tooltip container's max with in pixels.</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h3" class="mb-2 mt-4" customSize="text-lg font-bold md:text-xl lg:text-2xl"
		>Example</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
// Reference to the DefaultTooltip singleton
DefaultTooltip tooltip = DefaultTooltip.Instance;

// VisualElement that will display tooltip on hover
VisualElement tooltipOnHover = _uiDocument.rootVisualElement.Q<VisualElement>("TooltipOnHover");

// Create elements that will display in the tooltip
VisualElement image = new VisualElement();
image.AddToClassList("size-40");
image.style.backgroundImage = new StyleBackground(mySprite);
Label title = new Label("My Tooltip Title");
Label body = new Label("My Tooltip Desctiption");
VisualElement bottom = null;

// Tooltip colors
UIColor bgColor = new UIColor(UIColorName.SLATE, UIColorValue.V_800);
UIColor borderColor = new UIColor(UIColorName.SLATE, UIColorValue.V_200);

// Create a DefaultTooltipContainerSetup
var containerSetup = new DefaultTooltipContainerSetup(
	image,
	title,
	body,
	bottom,
	bgColor,
	borderColor
);

// Create Manipulator
DefaultTooltipManipulator manipulator = new DefaultTooltipManipulator(gameObject, tooltip);
manipulator.SetSetup(containerSetup);

// Add Manipulator, you can add same manipulator to multiple elements if needed
tooltipOnHover.AddManipulator(manipulator);`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
