<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import inventory_ingredients from '$lib/img/docs/views/inventory_ingredients.png';
	import gridview_hero from '$lib/img/docs/views/gridview_hero.png';

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
	>Views/ GridView</Heading
>
<div class="p-4">
	<p class="mb-4">The GridView{"<TItem>"} class is an abstract base class designed for creating paginated and filterable grid views. It displays items in a grid layout, handles pagination, can apply filters, and manage item selection.</p>
	<h2 class="my-4 text-xl font-bold md:text-2xl lg:text-3xl">Examples</h2>
	<a class="font-bold text-sky-400" href="/luna/views/inventory">InventoryView</a>
	<img alt="pausemenu" src={inventory_ingredients} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<span>Heroes</span>
	<img alt="pausemenu" src={gridview_hero} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<P>GridView is a large class with lots of properties so it can be complex, but each property is simple on it's own.</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Contructors</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
// GridView is an abstract class that extends UIView
public abstract class GridView<TItem> : UIView

public GridView(
      List<TItem> itemList, // Data source, list of items to display
      VisualTreeAsset itemSlotTemplate, // VisualTreeAsset to use as a template for each item slot
      GameObject parent, // Parent GameObject
      VisualElement parentElement, // Parent VisualElement
      VisualElement slotContainer, // Container VisualElement to hold the item slots, grid items will be added to this container
// UIView properties
      UIStartVisibility startVisibility = UIStartVisibility.Visible,
      VisualElement focusElement = null,
      float fadeDuration = 0.5F,
      EasingMode easingMode = EasingMode.EaseOutCirc,
      bool disableOtherViewsOnFadeIn = false,
      bool debug = false
)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Public Methods</Heading
	>
	// TODO
</div>
