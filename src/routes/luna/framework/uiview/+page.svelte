<script>
	import { Heading, P, A, Mark, Secondary, Button, Hr } from 'flowbite-svelte';

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
public UIView(
  GameObject parent, 
  VisualElement parentElement,
  UIStartVisibility startVisibility = UIStartVisibility.Visible, 
  VisualElement focusElement = null, 
  float fadeDuration = 0.5f,
  EasingMode easingMode = EasingMode.EaseOutCirc,
  bool debug = false
)`;
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl">UIView</Heading>
<div class="p-4">
	<P class="mb-4">
		The <strong class="font-bold">UIView</strong> is the base class responsible for managing the lifecycle
		and visibility of an UI Element. It provides control over UI visibility states, fade animations,
		and allows for custom actions during these transitions.
	</P>
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Constructor</Heading
	>
	<CodeBlock
		language="csharp"
		{code}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Table class="my-4 rounded border-4 border-stone-400">
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
					>Parent GameObject used to control lifecycle of the UIView.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>parentElement</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>VisualElement</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>The VisualElement that serves as the parent for this UIView.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>startVisibility</TableBodyCell>
				<TableBodyCell {tdClass}>UIStartVisibility</TableBodyCell>
				<TableBodyCell {tdClass}
					>The UIStartVisibility enum defines the possible initial visibility states of the
					parentElement.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>focusElement</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>VisualElement</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>The VisualElement element to focus whenever UIView becomes visible.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>fadeDuration</TableBodyCell>
				<TableBodyCell {tdClass}>float</TableBodyCell>
				<TableBodyCell {tdClass}
					>Specifies the duration of the fade transition, in seconds.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>easingMode</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>EasingMode</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Defines the easing effect applied during fade transitions.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>debug</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>bool</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Logs fade transitions, enable/disable events, and UI Actions.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Public Properties</Heading
	>
	<Table class="my-4 rounded border-4 border-stone-400">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Name</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Type</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>Parent</TableBodyCell>
				<TableBodyCell {tdClass}>GameObject</TableBodyCell>
				<TableBodyCell {tdClass}
					>Parent GameObject used to control lifecycle of the UIView.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>ParentElement</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>VisualElement</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>The VisualElement that serves as the parent for this UIView.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>LunaUIManager</TableBodyCell>
				<TableBodyCell {tdClass}
					><A color="text-sky-400 font-extrabold" href="/luna/framework/uimanager"
						>LunaUIManager</A
					></TableBodyCell
				>
				<TableBodyCell {tdClass}
					>LunaUIManager tracks interactable visual elements, enabling mass activation or
					deactivation within a UIView. You can also set a blocking element to prevent interaction
					with other elements until it is clicked.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>Fade</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					><A color="text-sky-400 font-extrabold" href="/luna/framework/fadeuielement"
						>FadeUIElement</A
					></TableBodyCell
				>
				<TableBodyCell tdClass={tdClasss}>Manage fade transitions of the UIView.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>IsEnabled</TableBodyCell>
				<TableBodyCell {tdClass}>bool</TableBodyCell>
				<TableBodyCell {tdClass}>todo</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>easingMode</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>EasingMode</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Defines the easing effect applied during fade transitions.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Public Methods</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>AddAction</Heading
	>
	<P>Adds a new action to the view's action list.</P>
	<P
		>If the view is currently faded in, the action's OnFadeIn method will be triggered immediately.</P
	>
	<P
		>The action will be automatically enabled or disabled in sync with the view's fade-in or
		fade-out state.</P
	>
	<P>Adds a new action to the view's action list.</P>
	<CodeBlock
		language="csharp"
		code={`public void AddAction(IUIViewAction action, bool activate = true)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	
	<Table class="my-4 rounded border-4 border-stone-400">
		<TableHead>
			<TableHeadCell class={tdheadClass}>Name</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Type</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>action</TableBodyCell>
				<TableBodyCell {tdClass}>IUIViewAction</TableBodyCell>
				<TableBodyCell {tdClass}
					>Action to add to the UIView.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell tdClass={tdClasss}>activate</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}>bool</TableBodyCell>
				<TableBodyCell tdClass={tdClasss}
					>Activates the Action immediately if the UIView is currently enabled. If the UIView is not enabled, the Action is not triggered even if this is true.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h4" class="my-2" customSize="text-base font-bold md:text-lg lg:text-xl"
		>Example</Heading
	>
	<P>Register an action that returns to the previous screen when the Escape key is pressed.</P>
	<CodeBlock
		language="csharp"
		code={`myUIView.AddAction(new UIViewActionEscape(ReturnToPreviousScreen));`}
		showHeader={true}
		showLineNumbers={true}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P class="my-2"
		>Learn more at <A color="text-sky-400 font-extrabold" href="/luna/framework/uiactions"
			>UI Actions</A
		>.</P
	>
	<P class="my-2"
		>See <A color="text-sky-400 font-extrabold" href="/luna/framework/examplemultipage"
			>Example: Multi Page UI</A
		> which demonstrates usage of UIViewActionEscape.</P
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>AddChild</Heading
	>
	<CodeBlock
		language="csharp"
		code={`public void AddChild(UIView child)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P
		>When you have nested UIViews with UI Actions, you might need to register their parent-child
		relationships.</P
	>
	<P
		>Whenever a parent UIView is enabled or disabled, it will trigger the UI Actions of its
		children.</P
	>
	<P class="my-2"
		>The <A color="text-sky-400 font-extrabold" href="/luna/framework/examplemultipage"
			>Example: Multi Page UI</A
		> also demonstrates parent-child relationships.</P
	>
</div>
