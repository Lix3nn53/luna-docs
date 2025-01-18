<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr, Li, List } from 'flowbite-svelte';
	import settings_system from '$lib/img/docs/views/settings_system.png';
	import settings_data from '$lib/img/docs/views/settings_data.jpg';
	import saveload from '$lib/img/docs/views/saveload.jpg';

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
	>Views/ Save & Load</Heading
>
<div class="p-4">
	<img alt="saveload" src={saveload} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />
	<P>GameSaveViewList works together with the GameSaveManager.</P>
	<Heading tag="h2" class="my-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>GameSaveViewList</Heading
	>
	<P
		>All you have to do implement abstract class GameSaveViewList according to your game's custom
		save data.</P
	>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Example</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
using UnityEngine.UIElements;
using CupkekGames.Core;

public class GameSaveViewListExample : GameSaveViewList<GameSaveDataExample>
{
	protected override GameSaveManager<GameSaveDataExample> GetSaveManager()
	{
		return GameSaveManagerExample.Instance;
	}

	protected override bool IsInGame()
	{
		// If MainMenu Scene is not loaded, we are not in game so return false to disable saving
		return !SceneLoader.Instance.IsLoaded("MainMenu");
	}

	protected override VisualElement SlotOne(int index, int saveSlot, GameSaveDataExample data)
	{
		VisualElement container = new();
		container.AddToClassList("flex-row");

		VisualElement containerLeft = new();
		container.Add(containerLeft);
		VisualElement containerRight = new();
		container.Add(containerRight);

		containerLeft.Add(new Label("Index: " + (index + 1)));
		containerLeft.Add(new Label("File: " + (saveSlot + 1)));

		containerRight.Add(new Label(data.SaveDate.ToString()));
		bool autosave = GameSaveManager.IsAutosave(saveSlot);
		containerRight.Add(new Label("Autosave: " + autosave));

		return container;
	}

	protected override VisualElement SlotTwo(int index, int saveSlot, GameSaveDataExample data)
	{
		return new Label("Gold: " + data.Gold);
	}

	protected override void OnLoadButtonClicked(int saveSlot, GameSaveDataExample slot)
	{
		GameSaveManager.CurrentSave.Data = slot;

		SceneLoader.Instance.LoadScene(2, SceneTransitionManager.Instance.Transitions.GetValue("FadeWithInput"));

		GameSaveView.ReturnClicked(); // unloads prefab
	}
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<P class="my-4">Thats it, check the Game Samples for implementation example.</P>
</div>
