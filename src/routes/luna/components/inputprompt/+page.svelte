<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import inputpromptImg from '$lib/img/docs/components/inputprompt.jpg';
	import inputdevicemanager from '$lib/img/docs/components/inputdevicemanager.jpg';
	import inputicondatabase from '$lib/img/docs/components/inputicondatabase.jpg';
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
	let tdClass = 'px-6 py-2 whitespace-normal font-medium bg-stone-600 min-w-48';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Components/ Input Prompt</Heading
>
<div class="p-4">
	<img alt="samples" src={input} class="mb-6 max-w-full rounded-xl border-4 xl:max-w-xl" />
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Attributes</Heading
	>
	<img alt="samples" src={inputpromptImg} class="mb-6 max-w-md rounded-xl border-4" /><Table
		class="rounded"
	>
		<TableHead>
			<TableHeadCell class={tdheadClass}>Attribute</TableHeadCell>
			<TableHeadCell class={tdheadClass}>Description</TableHeadCell>
		</TableHead>
		<TableBody tableBodyClass="divide-y">
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>InputActionName</TableBodyCell>
				<TableBodyCell {tdClass}>Name of input action to pick from input actions.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>OverrideIconSprite</TableBodyCell>
				<TableBodyCell {tdClass}
					>InputPrompt displays icon according to InputActionName. You can override it with this.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>OverrideIconText</TableBodyCell>
				<TableBodyCell {tdClass}
					>InputPrompt displays text according to InputActionName. You can override it with this.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>MinSize</TableBodyCell>
				<TableBodyCell {tdClass}>Min width and height of the icon.</TableBodyCell>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>ButtonIf</TableBodyCell>
				<TableBodyCell {tdClass}
					>List of InputIconControlScheme. If the list contains KeyboardMouse, the InputPrompt will
					automatically switch to being interactable so it can be clicked with mouse. However, when
					switching to a gamepad, it will no longer be interactable, ensuring that auto-navigation
					ignores it. This prevents navigation with d-pad from selecting the InputPrompt, which is
					typically not desirable.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>HideIf</TableBodyCell>
				<TableBodyCell {tdClass}
					>List of InputIconControlScheme. Hide the InputPrompt automatically on desired input
					control schemes.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>PlayerIndex</TableBodyCell>
				<TableBodyCell {tdClass}
					>Index of the player this InputPrompt should display input for. Used in multiplayer
					scenarios to show different player inputs.</TableBodyCell
				>
			</TableBodyRow>
			<TableBodyRow color="custom" class={tdrowClass}>
				<TableBodyCell {tdClass}>HideIfPlayerIndexMissing</TableBodyCell>
				<TableBodyCell {tdClass}
					>If true, hides the InputPrompt when the specified PlayerIndex doesn't have an active
					PlayerInput. Useful for dynamic multiplayer UI.</TableBodyCell
				>
			</TableBodyRow>
		</TableBody>
	</Table>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>InputIconControlScheme</Heading
	>
	<P>enum</P>
	<List tag="ul" class="space-y-1 py-2">
		<Li>KeyboardMouse</Li>
		<Li>Xbox</Li>
		<Li>PlayStation4</Li>
		<Li>PlayStation5</Li>
	</List>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Integration with InputDeviceManager</Heading
	>
	<P
		>InputPrompt works closely with <A
			class="font-bold text-sky-400"
			href="/luna/core/devicemanager">InputDeviceManager</A
		> which has 2 responsibilities:</P
	>
	<List tag="ul" class="space-y-1 py-2">
		<Li>Detecting input scheme changes to automatically update InputPrompt icons and texts.</Li>
		<Li>Connection between InputPrompt and InputIconDatabase.</Li>
		<Li
			>Managing player input registration and control scheme tracking for multiplayer scenarios.</Li
		>
	</List>
	<P class="mb-4">
		The InputPrompt automatically subscribes to InputDeviceManager events to update its display when
		players join/leave or when control schemes change.
	</P>
	<img
		alt="inputdevicemanager"
		src={inputdevicemanager}
		class="my-6 max-w-md rounded-xl border-4"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Integration with LunaUIManager</Heading
	>
	<P class="mb-4">
		InputPrompt integrates with <A class="font-bold text-sky-400" href="/luna/framework/uimanager"
			>LunaUIManager</A
		> to access the InputIconDatabase. The LunaUIManager provides the IconDatabase property which contains
		the input icons for different control schemes.
	</P>
	<P class="mb-4">
		When InputPrompt needs to display an icon, it queries the LunaUIManager's IconDatabase to get
		the appropriate sprite and text for the current control scheme.
	</P>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>InputIconDatabase</Heading
	>
	<P>Dictionaries of sprites for each control scheme.</P>
	<P
		>Icons used: <A
			color="text-sky-400 font-extrabold"
			href="https://www.kenney.nl/assets/input-prompts"
			target="_blank">https://www.kenney.nl/assets/input-prompts</A
		></P
	>
	<img alt="inputicondatabase" src={inputicondatabase} class="my-6 max-w-md rounded-xl border-4" />
</div>
