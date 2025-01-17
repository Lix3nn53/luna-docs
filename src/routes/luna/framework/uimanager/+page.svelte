<script>
	import { Heading, P, A, Alert, Button, Hr } from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';

	import uimanager from '$lib/img/docs/framework/uimanager.jpg';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Luna UI Manager</Heading
>
<div class="p-4">
	<img alt="uimanager" src={uimanager} class="mb-6 max-w-2xl rounded-xl border-4" />
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Settings</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Input Settings</Heading
	>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>Player Input</Heading
	>
	<P>
		A Player Input reference is required for the proper functioning of Escape Action
		<A class="font-bold text-sky-400" href="/luna/components/inputprompt">
			InputPromt
		</A>
		component.
	</P>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>Escape Action Names</Heading
	>
	<P>Names of InputActions that will trigger escape when performed. See
		<A class="font-bold text-sky-400" href="/luna/framework/uiactions#UIViewActionEscape">
			UIViewActionEscape
		</A>
		for more info.
	</P>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>Input Icon Database</Heading
	>
	<P>Input icons for 
		<A class="font-bold text-sky-400" href="/luna/components/inputprompt">
			InputPromt
		</A>
		components.
	</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>UI Element Manager Settings</Heading
	>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>Blacklist</Heading
	>
	<P>List of VisualElement names to ignore. UIElementManager automatically adds hover and click sounds to focusable elements. 
		Add elements here if you cannot disable their focusable state but do not want sounds applied to them.</P>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>UI Element Manager</Heading
	>
	<P class="mb-4">UI Element Manager is a feature within the Luna UI Manager.</P>
	<P class="mb-4">
		Manages the registration and state of VisualElement instances within a hierarchy of
		VisualElement containers. It provides functionality for <strong class="font-bold text-rose-400"
			>enabling and disabling groups of elements</strong
		>, which is particularly useful for managing UI navigation.
	</P>
	<P class="mb-4">
		Automatically adds <strong class="font-bold text-rose-400">audio feedback</strong> to interactable
		elements like buttons.
	</P>
	<P class="mb-4">
		Additionally, it includes functionality for setting a <strong class="font-bold text-rose-400"
			>blocker element</strong
		>.
	</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Public Methods</Heading
	>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>SetBlocker</Heading
	>
	<P
		>Disables all UI elements and sets a specified VisualElement as the active blocker, ensuring it
		remains enabled and interactive. When clicked, it will re-enable all previously disabled
		elements.</P
	>
	<CodeBlock
		language="csharp"
		code={`
public void SetBlocker(VisualElement blocker)
// or
public void SetBlocker(string elementName)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>SetEnabledAll</Heading
	>
	<Alert border>
		<div class="flex flex-row">
			<i class="fa-solid fa-circle-info fa-2xl mr-4 mt-4"></i>
			<div>
				<P
					>The <A
						class="font-bold text-sky-400"
						href="/luna/framework/uiactions#UIViewActionEnableElements"
						>UIViewActionEnableElements</A
					> uses these functions.</P
				>
			</div>
		</div>
	</Alert>
	<P></P>
	<CodeBlock
		language="csharp"
		code={`
public List<VisualElement> SetEnabledAll(bool enabled, VisualElement except = null)
// or
public List<VisualElement> SetEnabledAll(bool enabled, List<VisualElement> except)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>SetEnabledPage</Heading
	>
	<P></P>
	<CodeBlock
		language="csharp"
		code={`public void SetEnabledPage(VisualElement page, bool enabled)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>RegisterPage</Heading
	>
	<Alert border>
		<div class="flex flex-row">
			<i class="fa-solid fa-circle-info fa-2xl mr-4 mt-4"></i>
			<div>
				<P>You <strong class="font-bold text-rose-400">don't need to manually register</strong> elements when using UIViews.</P>
				<P>However, for documentation purposes, the functions are detailed here.</P>
			</div>
		</div>
	</Alert>
	<P></P>
	<CodeBlock
		language="csharp"
		code={`public void RegisterPage(VisualElement parent)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>UnregisterPage</Heading
	>
	<P
		>Returns the predefined duration of fade transitions. Note that it does not reflect the current
		active transition duration.</P
	>
	<CodeBlock
		language="csharp"
		code={`public void UnregisterPage(VisualElement parent)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>GetPage</Heading
	>
	<P></P>
	<CodeBlock
		language="csharp"
		code={`public HashSet<VisualElement> GetPage(VisualElement parent)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>RegisterElement</Heading
	>
	<P></P>
	<CodeBlock
		language="csharp"
		code={`public void RegisterElement(VisualElement parent, VisualElement item)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h4" class="my-2" customSize="text-md font-bold md:text-lg lg:text-xl ml-4"
		>UnregisterElement</Heading
	>
	<P></P>
	<CodeBlock
		language="csharp"
		code={`public void UnregisterElement(VisualElement parent, VisualElement item)`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
