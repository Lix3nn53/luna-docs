<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';

	import prefabloader from '$lib/img/docs/core/prefabloader.jpg';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Systems/ Game Save Manager</Heading
>
<div class="p-4">
	<P class="pb-4">GameSaveManager{"<TSaveData>"} is an abstract class designed for managing game save data in Unity. It facilitates automatic saving, loading, and deletion of game save files while providing flexibility for customization based on specific save data types.</P>
	<Heading tag="h3" class="my-2" customSize="text-lg font-bold md:text-xl lg:text-2xl ml-2"
		>Mock implementation from demo</Heading
	>
	<CodeBlock
		language="csharp"
		code={`
using System;
using System.Collections.Generic;
using System.Linq;
using CupkekGames.Core;
using CupkekGames.Systems;
using UnityEngine;

namespace CupkekGames.Luna.Library
{
  [CreateAssetMenu(fileName = "GameSaveManagerExample", menuName = "CupkekGames/Samples/GameSaveManagerExample")]
  public class GameSaveManagerExample : GameSaveManager<GameSaveDataExample>
  {
    [MultiLineHeader("This is a mockup. The save system is not included.")]
    [SerializeField] private int _mockSaveAmount = 50;
    private Dictionary<string, GameSaveDataExample> _saveMockUp = new Dictionary<string, GameSaveDataExample>();
    public Dictionary<string, GameSaveDataExample> SaveMockUp => _saveMockUp;

    public void OnEnable()
    {
      DateTime endDate = DateTime.Now;
      DateTime startDate = endDate.AddMonths(-3);

      for (int saveSlot = 0; saveSlot < _mockSaveAmount; saveSlot++)
      {
        string fileName = GetSaveFileName(saveSlot);

        GameSaveDataExample data = new GameSaveDataExample();

        data.Gold = UnityEngine.Random.Range(100, 1000);

        data.SaveDate = GetRandomDate(startDate, endDate);

        _saveMockUp.Add(fileName, data);
      }
    }

    public DateTime GetRandomDate(DateTime startDate, DateTime endDate)
    {
      if (startDate > endDate)
        throw new ArgumentException("startDate should be less than or equal to endDate");

      // Get the range of ticks between the two dates
      long range = (endDate - startDate).Ticks;

      // Generate a random number of ticks within this range
      var random = new System.Random();
      long randomTicks = (long)(random.NextDouble() * range);

      // Return the random date by adding random ticks to the start date
      return startDate.AddTicks(randomTicks);
    }


    protected override GameSaveDataExample GetNewSave()
    {
      return new GameSaveDataExample();
    }
    protected override GameSaveDataExample LoadFromFile(string fileName)
    {
      return _saveMockUp[fileName];
    }

    protected override List<string> GetAllFileNames()
    {
      return _saveMockUp.Keys.ToList();
    }

    protected override void OnDeleteRequest(int saveSlot, string fileName)
    {
      _saveMockUp.Remove(fileName);
    }

    protected override void OnSaveRequest(int saveSlot, string fileName, GameSaveDataExample data)
    {
      bool autosave = IsAutosave(saveSlot);
      if (autosave)
      {
        GameSaveEvents.AutosaveStart?.Invoke();
      }

      GameSaveDataExample clone = new();

      clone.SaveDate = DateTime.Now;
      clone.SaveSlot = -1;

      clone.PlayerName = data.PlayerName;
      clone.Gold = data.Gold;
      clone.Diamond = data.Diamond;
      clone.Exp = data.Exp;
      clone.Lvl = data.Lvl;
      clone.ExpReq = data.ExpReq;
      clone.NotificationHistory = data.NotificationHistory;

      if (_saveMockUp.ContainsKey(fileName))
      {
        _saveMockUp[fileName] = clone;
      }
      else
      {
        _saveMockUp.Add(fileName, clone);
      }

      if (autosave)
      {
        GameSaveEvents.AutosaveComplete?.Invoke();
      }
    }

    protected override string GetFileExtenstion()
    {
      return "save";
    }
  }
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
