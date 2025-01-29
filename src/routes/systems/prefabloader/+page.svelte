<script>
	import { Heading, P, A, Mark, Secondary, GradientButton, Hr } from 'flowbite-svelte';

	import { CodeBlock } from 'svhighlight';
	import 'highlight.js/styles/base16/papercolor-dark.css';

	import prefabloader from '$lib/img/docs/core/prefabloader.jpg';
</script>

<Heading tag="h1" customSize="text-2xl font-extrabold md:text-3xl lg:text-4xl"
	>Core/ Prefab Loader</Heading
>
<div class="p-4">
	<P>Load and track prefabs. Has normal and addressable version. With minimal scripting, you can add some useful inspector buttons to search and find all prefabs at once.</P>
	<Heading tag="h2" class="mb-4" customSize="text-xl font-bold md:text-2xl lg:text-3xl"
		>Addressable Example from Hero Manager</Heading
	>
	<img alt="prefabloader" src={prefabloader} class="mb-6 xl:max-w-xl max-w-full rounded-xl border-4" />

	<CodeBlock
		language="csharp"
		code={`
using CupkekGames.Systems.UI;

namespace CupkekGames.HeroManager
{
  public class UIPrefabLoader : UIPrefabLoaderAddressable<UIPrefabType>
  {
    private static UIPrefabLoader _instance;

    public static UIPrefabLoader Instance
    {
      get
      {
        return _instance;
      }
    }

    protected override void Awake()
    {
      if (_instance == null)
      {
        _instance = this;
        DontDestroyOnLoad(gameObject); // Optional: keep this instance across scenes
      }
      else
      {
        Destroy(gameObject); // Destroy duplicate instances
        return;
      }

      base.Awake();
    }

    private void OnDestroy()
    {
      if (_instance == this)
      {
        _instance = null;
      }
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
using UnityEditor;
using CupkekGames.Systems.Editor;
using CupkekGames.Luna;
using System;

namespace CupkekGames.HeroManager.Editor
{
    [CustomEditor(typeof(UIPrefabLoader), true)]
    public class UIPrefabLoaderEditor : PrefabLoaderAddressableEditor<UIPrefabType, UIViewComponent>
    {
        public override UIPrefabType GetKeyFromFileName(string name)
        {
            if (Enum.TryParse(name, out UIPrefabType enumValue))
            {
                // Conversion succeeded
                return enumValue;
            }
            else
            {
                // Handle the case where conversion failed
                throw new Exception("Invalid enum string: " + name);
            }
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
