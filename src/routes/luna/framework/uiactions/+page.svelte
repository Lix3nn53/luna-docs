<script>
	import { Heading, P, A, Alert, Button, Hr, Li, List } from 'flowbite-svelte';

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
	let tdrowClass = 'border-stone-200';
	let tdClass = 'px-6 py-4 whitespace-normal font-medium bg-stone-700 min-w-48';
	let tdClasss = 'px-6 py-4 whitespace-normal font-medium bg-stone-800 min-w-48';

	let code = `
public FadeUIElement(
  MonoBehaviour coroutineRunner, 
  VisualElement visualElement, 
  EasingMode easingMode = EasingMode.EaseOutCirc, 
  bool debug = false)`;
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">UI Actions</Heading>
<div class="p-4">
	<P class="mb-4">
		UI Actions are a core feature of the <strong class="font-bold">UIView</strong> system that allow
		developers to link custom behaviors to the view's visibility transitions (fade in/out). These
		actions implement the <strong class="font-bold">IUIViewAction interface</strong> and are
		<strong class="font-bold text-rose-400"
			>executed automatically whenever the UIView's visibility changes.</strong
		>
	</P>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Lifecycle</Heading
	>
	<List tag="ul" class="space-y-1">
		<Li
			><strong class="font-bold text-yellow-400">OnFadeIn:</strong> Called when the UIView becomes visible
			(fades in).</Li
		>
		<Li
			><strong class="font-bold text-yellow-400">OnFadeOut:</strong> Called when the UIView becomes hidden
			(fades out).</Li
		>
	</List>
	<P class="mb-4"
		>This provides a simple, event-driven way to manage UI behavior that needs to sync with the
		view's state.</P
	>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Default Actions</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
	id="UIViewActionEscape">UIViewActionEscape</Heading
	>
	<P
		>This class allows you to push and pop a custom action(System.Action) into the
		InputEscapeManager in sync with the visibility of an UIView.</P
	>
	<Heading tag="h4" class="my-2" customSize="text-base font-bold md:text-lg lg:text-xl"
		>Constructor</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public UIViewActionEscape(Action onEscape = null, bool debug = false)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-base font-bold md:text-lg lg:text-xl"
		>Example</Heading
	>
	<CodeBlock
		language="csharp"
		code={`UIView.AddAction(new UIViewActionEscape(ReturnToPreviousScreen));`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P class="my-2"
		>See <A color="text-sky-400 font-extrabold" href="/luna/framework/examplemultipage"
			>Example: Multi Page UI</A
		> for more detailed example.</P
	>
	<Heading
		tag="h3"
		class="my-2"
		customSize="text-lg font-bold md:text-xl lg:text-2xl"
		id="UIViewActionEnableElements">UIViewActionEnableElements</Heading
	>
	<P>Disables `VisualElements` during `OnFadeIn` and re-enables them during `OnFadeOut`.</P>
	<P
		>This is particularly useful for UI navigation with keys when opening a modal or screen on top
		of another view.</P
	>
	<P
		>Add this action to a modal and pass in the parent `VisualElement` of the underlying view. This
		will disable the elements of the underlying view when the modal becomes visible and re-enable
		them when the modal fades out.</P
	>
	<Heading tag="h4" class="my-2" customSize="text-base font-bold md:text-lg lg:text-xl"
		>Constructor</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public UIViewActionEnableElements(bool enabled, VisualElement except = null)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-base font-bold md:text-lg lg:text-xl"
		>Example</Heading
	>
	<CodeBlock
		language="csharp"
		code={`myModal.AddAction(new UIViewActionEnableElements(false, underlyingView.ParentElement));`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P class="my-2"
		>See <A color="text-sky-400 font-extrabold" href="/luna/framework/examplemultipage"
			>Example: Multi Page UI</A
		> for more detailed example.</P
	>
</div>
