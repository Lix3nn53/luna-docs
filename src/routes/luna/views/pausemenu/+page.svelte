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
	<img alt="pausemenu" src={pausemenu} class="mb-6 max-w-2xl rounded-xl border-4" />
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
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl"
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
</div>
