<script>
	import { Heading, P, A, Alert, Secondary, GradientButton, Hr } from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Core/ Input Escape Manager</Heading
>

<P class="py-4">InputEscapeManager is a static class that manages escape actions in a stack-like manner. It allows pushing, popping, and executing registered escape actions. This system ensures that only the most recent escape action is executed when triggered.</P>
<Alert border>
	<div class="flex flex-row">
		<i class="fa-solid fa-circle-info fa-2xl mr-4 mt-4"></i>
		<div>
			<P class="mb-4"
				><A class="font-bold text-sky-400" href="/luna/framework/uiactions#UIViewActionEscape">
					UIViewActionEscape
				</A> uses InputEscapeManager. While Luna UI uses this to exit from UIViews, it can also be used for other purposes beyond UI.</P
			>
		</div>
	</div>
</Alert>
<div class="p-4">
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Public Methods</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Push</Heading
	>
	<P class="pb-4">You can push an action onto the escape stack, optionally providing a unique key and an insertion index.</P>
	<CodeBlock
		language="csharp"
		code="
// Method signature:
public static void Push(Action action, Guid? key = null, int insert = -1)
// Simple usage:
InputEscapeManager.Push(() => Debug.Log({"Escape action triggered"}));
// With a specific key:
Guid actionKey = Guid.NewGuid();
InputEscapeManager.Push(() => Debug.Log({"Keyed escape action"}), actionKey);
// Inserting at a specific position:
InputEscapeManager.Push(() => Debug.Log({"Inserted action"}), null, 0);
"
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Popping an Escape Action</Heading
	>
	<P class="pb-4">Pops and executes the most recent escape action.</P>
	<CodeBlock
		language="csharp"
		code="
// Simple usage:
InputEscapeManager.Pop();
// Popping a specific action by key, ignoring order:
InputEscapeManager.Pop(actionKey);
// Popping without execution:
InputEscapeManager.PopWithoutExecute(actionKey);
"
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Blocking Escape Execution</Heading
	>
	<P class="py-4">Temporarily block escape actions from executing</P>
	<CodeBlock
		language="csharp"
		code={"//To temporarily block escape actions from executing:\nInputEscapeManager.SetBlocked(true);\n//To allow execution again:\nInputEscapeManager.SetBlocked(false);"}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Events</Heading
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>InputEscapeEvent</Heading
	>
	Triggered when an escape action occurs. By default, it calls Pop() to execute the last action. Can be triggered manually to execute the last action.
</div>
