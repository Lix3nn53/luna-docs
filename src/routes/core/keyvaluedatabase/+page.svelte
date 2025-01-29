<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';

	import keyvaluedatabase from '$lib/img/docs/core/keyvaluedatabase.jpg';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Core/ KeyValue Database</Heading
>
<div class="p-4">
	<P>Basicly a serialized functionality with an additions. With minimal scripting, you can add some useful inspector buttons to automatically fill the dictionary. Very useful for large dictionaries like item database.</P>
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Example from Hero Manager</Heading
	>
	<img alt="keyvaluedatabase" src={keyvaluedatabase} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />

	
	<CodeBlock
		language="csharp"
		code={`
using CupkekGames.Core;
using CupkekGames.Luna;
using UnityEngine;

namespace CupkekGames.HeroManager
{
  public class ItemDatabaseIngredient : KeyValueDatabaseMonoSO<string, IngredientSO>
  {
    public InventoryItemDefinition GetItemDefinition(string key)
    {
      if (string.IsNullOrEmpty(key))
      {
        Debug.Log("Null key");
        return null;
      }

      if (!ContainsKey(key))
      {
        Debug.Log("Ingredient doesnt exist: " + key);
        return null;
      }

      return GetValue(key).ItemDefinition;
    }
  }
}`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
	<CodeBlock
		language="csharp"
		code={`
#if UNITY_EDITOR
using CupkekGames.Core.Editor;
using UnityEditor;

namespace CupkekGames.HeroManager.Editor
{
    [CustomEditor(typeof(ItemDatabaseIngredient))]
    public class ItemDatabaseIngredientEditor : KeyValueDatabaseMonoSOEditor<string, IngredientSO>
    {
        public override string GetKeyFromFileName(string name)
        {
            return name;
        }
    }
}
#endif`}
		showHeader={false}
		showLineNumbers={false}
		background="bg-zinc-900"
		headerClasses="bg-zinc-800 text-white/80 text-xs font-bold"
	/>
</div>
