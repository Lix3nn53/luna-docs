<script>
	import {
		Heading,
		P,
		A,
		Mark,
		Secondary,
		GradientButton,
		Hr,
		Li,
		List,
		Alert
	} from 'flowbite-svelte';
	import pausemenu from '$lib/img/docs/views/pausemenu.jpg';

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
	>Views/ Pause Menu</Heading
>
<div class="p-4">
	<img alt="pausemenu" src={pausemenu} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<P
		>An example implementation that you can use directly or as a starting point. You can refer to
		the demo game samples to see it in action or see the implementation details.</P
	>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>PauseMenuView</Heading
	>
	<P>Base class with buttons:</P>
	<List tag="ul" class="space-y-1 py-2">
		<Li>Continue</Li>
		<Li>Load Game</Li>
		<Li>Settings</Li>
		<Li>Main Menu</Li>
		<Li>Quit</Li>
	</List>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Example</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
using UnityEngine;
using CupkekGames.Core;

public class PauseMenuViewExample : PauseMenuView
{
	[Header("Prefab Keys")]
	[SerializeField] string _settingsMenuKey = "Settings";
	[SerializeField] string _loadMenuKey = "SaveLoad";

	private void OnButtonContinueClicked()
	{
		FadeOutThenDestroy();
	}

	protected override void OnButtonLoadGameClicked()
	{
		UIPrefabLoaderString.Instance.Instantiate(_loadMenuKey);
	}

	protected override void OnButtonSettingsClicked()
	{
		UIPrefabLoaderString.Instance.Instantiate(_settingsMenuKey);
	}

	protected override void OnButtonMainMenuClicked()
	{
		SceneLoader.Instance.LoadScene(1, SceneTransitionManager.Instance.Transitions.GetValue("Fade"));
	}

	protected override void OnButtonQuitGameClicked()
	{
		Application.Quit();
	}
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>PauseMenuEscapeAction</Heading
	>
	<P>Example Usage:</P>
	<P>In a visual novel, you might want to prevent going back before the dialogue finishes. Previously, using InputEscapeManager.SetBlocked(true) would block all escape actions (including opening the pause menu). With this new class, you can add the pause menu action to the end of the stack so that the pause menu remains accessible while blocking other back actions.</P>

</div>
