<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import tooltip from '$lib/img/docs/gallery/luna_tooltip.jpg';
	import tooltip_compare from '$lib/img/docs/components/tooltip_compare.jpg';
	import tooltip_inspector from '$lib/img/docs/components/tooltip_inspector.jpg';

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
	<p>The tooltip is designed to handle a wide range of scenarios.</p>
	
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl">Features</Heading>
	<List class="list-disc pl-6">
		<Li>Smooth size and position updates with configurable <Mark>fade settings</Mark></Li>
		<Li>Smart <Mark>auto-positioning</Mark> that prevents tooltips from going off-screen</Li>
		<Li>Display <Mark>multiple columns</Mark> simultaneously, perfect for comparing items in inventory with equipped gear</Li>
		<Li>Support for <Mark>nested tooltips</Mark> with customizable locking behavior</Li>
		<Li><Mark>Object pooling</Mark> for optimal performance with many tooltips</Li>
	</List>
	
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
				<TableBodyCell {tdClass}>Fade Duration</TableBodyCell>
				<TableBodyCell {tdClass}>Duration of fade animation.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Fade Easing Mode</TableBodyCell>
				<TableBodyCell {tdClass}
					>Easing mode of fade animation.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Tooltip Guide</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Class Controls</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
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
				<TableBodyCell {tdClass}>Position tooltip to the bottom of the VisualElement.</TableBodyCell>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
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
	
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>TooltipController</Heading
	>
	<P
		>TooltipController is a MonoBehaviour that keeps track of Tooltip element.</P
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>TooltipManipulator</Heading
	>
	<img alt="samples" src={tooltip_compare} class="mb-4 xl:max-w-xl max-w-full rounded-xl border-4" />
	<P
		>Add the TooltipManipulator to the VisualElements you want to display a tooltip for when they
		are hovered over or focused.</P
	>
	<CodeBlock
		language="csharp"
		code={`
// Create manipulator with multiple columns, as demonstrated in the item comparison tooltip example above.
public TooltipManipulator(GameObject parent, TooltipController tooltipController, List<TooltipContainerSetup> setups);

// Create manipulator with one column
var manipulator = public TooltipManipulator(GameObject parent, TooltipController tooltipController);
manipulator.SetSetup(setup);

// myElement will show tooltip on hover
myElement.AddManipulator(manipulator);`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P class="pt-4"
		>This will display the tooltip we created when myElement is hovered over or focused. As you can
		see, the Tooltip itself is very simple.</P
	>
	<Heading tag="h4" class="mb-2" customSize="text-md font-bold md:text-lg lg:text-xl"
		>Constructor</Heading
	>
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
				<TableBodyCell {tdClass}>tooltipController</TableBodyCell>
				<TableBodyCell {tdClass}>TooltipController</TableBodyCell>
				<TableBodyCell {tdClass}>Reference to the tooltip controller.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>setup</TableBodyCell>
				<TableBodyCell {tdClass}>TooltipContainerSetup</TableBodyCell>
				<TableBodyCell {tdClass}>Container setup for a column. See below for details.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table><br />
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>TooltipContainerSetup</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
// Constructor of TooltipContainerSetup
public TooltipContainerSetup(
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
// Reference to the TooltipController
[SerializeField] private TooltipController _tooltipController;

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

// Create a TooltipContainerSetup
var containerSetup = new TooltipContainerSetup(
	image,
	title,
	body,
	bottom,
	bgColor,
	borderColor
);

// Create Manipulator
TooltipManipulator manipulator = new TooltipManipulator(gameObject, _tooltipController);
manipulator.SetSetup(containerSetup);

// Add Manipulator, you can add same manipulator to multiple elements if needed
tooltipOnHover.AddManipulator(manipulator);`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
